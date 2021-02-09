---
title: Correspondance des accolades dans un service de langage hérité | Microsoft Docs
description: En savoir plus sur la correspondance des accolades dans un service de langage hérité, qui vous permet de suivre les éléments de langage qui doivent se produire ensemble, tels que les parenthèses et les accolades.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2bfcb9fdd7eff132d02c7d14be729cd871c8dd8e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905918"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Correspondance des accolades dans un service de langage hérité
La correspondance des accolades permet au développeur de suivre les éléments de langage qui doivent se produire ensemble, tels que des parenthèses et des accolades. Quand un développeur entre une accolade fermante, l’accolade ouvrante est mise en surbrillance.

 Vous pouvez faire correspondre deux ou trois éléments à coexistence, appelés paires et triples. Les triplets sont des ensembles de trois éléments à coexistence. Par exemple, en C#, l' `foreach` instruction forme un triple : `foreach()` , `{` et `}` . Les trois éléments sont mis en surbrillance lorsque l’accolade fermante est tapée.

 Les services de langage hérités sont implémentés dans le cadre d’un VSPackage, mais la meilleure façon d’implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter la correspondance des accolades, consultez [procédure pas à pas : afficher les accolades correspondantes](../../extensibility/walkthrough-displaying-matching-braces.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser la nouvelle API Editor dès que possible. Cela améliore les performances de votre service de langage et vous permet de tirer parti des nouvelles fonctionnalités de l’éditeur.

 La <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe prend en charge les deux paires et triples avec les <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> méthodes et.

## <a name="implementation"></a>Implémentation
 Le service de langage doit identifier tous les éléments correspondants dans le langage, puis localiser toutes les paires correspondantes. Cela s’effectue généralement en implémentant <xref:Microsoft.VisualStudio.Package.IScanner> pour détecter un langage correspondant, puis en utilisant la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode pour mettre en correspondance les éléments.

 La <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> méthode appelle le scanneur pour incorporer la ligne et retourner le jeton juste avant le signe insertion. Le scanneur indique qu’une paire d’éléments de langage a été trouvée en définissant une valeur de déclencheur de jeton <xref:Microsoft.VisualStudio.Package.TokenTriggers> sur le jeton actuel. La <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> méthode appelle la méthode <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> qui appelle à son tour la <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> méthode avec la valeur de raison de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason> pour localiser l’élément de langage correspondant. Lorsque l’élément de langage correspondant est trouvé, les deux éléments sont mis en surbrillance.

 Pour obtenir une description complète de la façon dont la saisie d’une accolade déclenche la mise en surbrillance des accolades, consultez la section *exemple d’opération d’analyse* dans l’article analyseur et analyseur de service de [langage hérité](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

## <a name="enable-support-for-brace-matching"></a>Activer la prise en charge de la correspondance des accolades
 L' <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attribut peut définir les entrées de Registre **MatchBraces**, **MatchBracesAtCaret** et **ShowMatchingBrace** qui définissent les propriétés correspondantes de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. Les propriétés de préférence de langue peuvent également être définies par l’utilisateur.

|Entrée de Registre|Propriété|Description|
|--------------------|--------------|-----------------|
|MatchBraces|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Active la correspondance des accolades.|
|MatchBracesAtCaret|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Active la correspondance des accolades au fur et à mesure du déplacement du signe insertion.|
|ShowMatchingBrace|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Met en surbrillance l'accolade correspondante.|

## <a name="match-conditional-statements"></a>Faire correspondre les instructions conditionnelles
 Vous pouvez faire correspondre des instructions conditionnelles, telles que `if` , `else if` , et `else` , ou,,, `#if` `#elif` `#else` `#endif` de la même façon que des délimiteurs correspondants. Vous pouvez sous- <xref:Microsoft.VisualStudio.Package.AuthoringSink> créer la classe et fournir une méthode qui peut ajouter des étendues de texte ainsi que des délimiteurs au tableau interne d’éléments correspondants.

## <a name="set-the-trigger"></a>Définir le déclencheur
 L’exemple suivant montre comment détecter les parenthèses correspondantes, les accolades et les accolades, et comment définir le déclencheur pour celui-ci dans le scanneur. La <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> méthode sur la <xref:Microsoft.VisualStudio.Package.Source> classe détecte le déclencheur et appelle l’analyseur pour trouver la paire correspondante (consultez la section *recherche de la correspondance* dans cet article). Cet exemple est fourni à titre d’illustration uniquement. Elle suppose que votre scanneur contient une méthode `GetNextToken` qui identifie et retourne des jetons à partir d’une ligne de texte.

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

## <a name="match-the-braces"></a>Faire correspondre les accolades
 Voici un exemple simplifié pour la correspondance des éléments de langage `{ }` , `( )` , et `[ ]` , et l’ajout de leurs étendues à l' <xref:Microsoft.VisualStudio.Package.AuthoringSink> objet. Cette approche n’est pas une approche recommandée pour l’analyse du code source. C’est à titre d’illustration uniquement.

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
- [Fonctionnalités du service de langage hérité](../../extensibility/internals/legacy-language-service-features1.md)
- [Analyseur et analyseur de service de langage hérité](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
