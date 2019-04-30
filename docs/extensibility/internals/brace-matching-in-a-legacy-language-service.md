---
title: Accolades correspondantes dans un Service de langage hérité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d83a4c3d9c070f77a6a13b28da0a57dbe6c48be0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63415354"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Accolades correspondantes dans un service de langage hérité
Correspondance d’accolade permet le développeur à effectuer le suivi des éléments de langage qui doivent se produire ensemble, telles que les parenthèses et les accolades. Lorsqu’un développeur entre une accolade fermante, l’accolade ouvrante est mis en surbrillance.

 Vous pouvez faire correspondre deux ou trois éléments qui se produisent conjointement, appelées paires et triples. Triplets sont des ensembles de trois éléments qui se produisent conjointement. Par exemple, en c#, le `foreach` instruction constitue un triple : `foreach()`, `{`, et `}`. Les trois éléments sont mis en surbrillance quand l’accolade fermante est tapée.

 Services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter les accolades correspondantes, consultez [procédure pas à pas : Affichage d’accolades correspondantes](../../extensibility/walkthrough-displaying-matching-braces.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.

 Le <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe prend en charge les deux paires et triple avec la <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> et <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> méthodes.

## <a name="implementation"></a>Implémentation
 Le service de langage doit identifier tous les éléments de mise en correspondance dans la langue et recherchez toutes les paires correspondantes. Cela est généralement effectuée en implémentant <xref:Microsoft.VisualStudio.Package.IScanner> pour détecter une langue de mise en correspondance et puis en utilisant la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode pour faire correspondre les éléments.

 Le <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> méthode appelle le moteur d’analyse pour marquer la ligne et de retourner le jeton juste avant le signe insertion. L’analyseur indique qu’une paire d’élément de langage a été trouvée en définissant une valeur de jeton de déclencheur de <xref:Microsoft.VisualStudio.Package.TokenTriggers> sur le jeton actuel. Le <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> les appels de méthode le <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> méthode qui appelle à son tour le <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> méthode avec la valeur de motif de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason> pour rechercher l’élément de langage correspondant. Lorsque l’élément de langage correspondant est trouvé, les deux éléments sont mis en surbrillance.

 Pour obtenir une description complète de la taper une accolade déclenche la mise en surbrillance des accolades, consultez le *opération d’analyse exemple* section dans l’article [Analyseur de service de langage hérité et scanneur](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

## <a name="enable-support-for-brace-matching"></a>Activer la prise en charge pour la correspondance des accolades
 Le <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attribut peut définir le **MatchBraces**, **MatchBracesAtCaret**, et **ShowMatchingBrace** les entrées de Registre qui définit les propriétés correspondantes de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. Propriétés de préférence de langue peuvent également être définies par l’utilisateur.

|Entrée de Registre|Propriété|Description|
|--------------------|--------------|-----------------|
|MatchBraces|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Active la correspondance des accolades.|
|MatchBracesAtCaret|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Correspondance d’accolade permet que le curseur se déplace.|
|ShowMatchingBrace|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Met en surbrillance l’accolade correspondante.|

## <a name="match-conditional-statements"></a>Instructions conditionnelles de correspondance
 Vous pouvez faire correspondre les instructions conditionnelles, telles que `if`, `else if`, et `else`, ou `#if`, `#elif`, `#else`, `#endif`, dans la même façon que des délimiteurs. Vous pouvez créer une sous-classe la <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe et fournir une méthode qui peut ajouter du texte s’étend sur ainsi que des délimiteurs dans le tableau interne d’éléments correspondants.

## <a name="set-the-trigger"></a>Définissez le déclencheur
 L’exemple suivant montre comment détecter la correspondance des parenthèses, des accolades et crochets et définissant le déclencheur pour celui-ci dans le scanneur. Le <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> méthode sur le <xref:Microsoft.VisualStudio.Package.Source> classe détecte le déclencheur et appelle l’analyseur pour rechercher la paire correspondante (voir la *recherche la correspondance* dans cet article). Cet exemple est uniquement à des fins d’illustration. Il suppose que le scanneur contient une méthode `GetNextToken` qui identifie et retourne les jetons à partir d’une ligne de texte.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private const string braces = "()[]{}";
        private Lexer lex;

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false;
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char firstChar = token[0];
                if (Char.IsPunctuation(firstChar) && token.Length > 0)
                {
                    if (braces.IndexOf(firstChar) != -1)
                    {
                        tokenInfo.Trigger = TokenTriggers.MatchBraces;
                    }
                }
            }
            return foundToken;
        }
```

## <a name="match-the-braces"></a>Correspondre les accolades
 Voici un exemple simplifié pour la mise en correspondance les éléments de langage `{ }`, `( )`, et `[ ]`et en ajoutant leurs étendues à la <xref:Microsoft.VisualStudio.Package.AuthoringSink> objet. Cette approche n’est pas une approche recommandée pour l’analyse de code source ; Il est uniquement à des fins d’illustration.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class Parser
    {
         private IList<TextSpan[]> m_braces;
         public IList<TextSpan[]> Braces
         {
             get { return m_braces; }
         }
         private void AddMatchingBraces(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             if IsMatch(braceSpan1, braceSpan2)
                 m_braces.Add(new TextSpan[] { braceSpan1, braceSpan2 });
         }

         private bool IsMatch(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             //definition for matching here
          }
    }

    public class TestLanguageService : LanguageService
    {
         Parser parser = new Parser();
         Source source = (Source) this.GetSource(req.FileName);

         private AuthoringScope ParseSource(ParseRequest req)
         {
             if (req.Sink.BraceMatching)
             {
                 if (req.Reason==ParseReason.MatchBraces)
                 {
                     foreach (TextSpan[] brace in parser.Braces)
                     {
                         req.Sink.MatchPair(brace[0], brace[1], 1);
                     }
                 }
             }
             return new TestAuthoringScope();
         }
    }
}
```

## <a name="see-also"></a>Voir aussi
- [Fonctionnalités de service de langage hérité](../../extensibility/internals/legacy-language-service-features1.md)
- [Scanneur et Analyseur de service de langage hérité](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)