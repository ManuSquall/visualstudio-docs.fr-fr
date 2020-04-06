---
title: Brace Matching in a Legacy Language Service (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0081be3e3ab5a53f7d85f77475d4288aa5c87092
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709815"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Brace correspondant dans un service linguistique hérité
L’appariement des accolades aide le développeur à suivre les éléments de langage qui doivent se produire ensemble, tels que les parenthèses et les accolades bouclées. Lorsqu’un développeur entre dans une accolade de fermeture, l’attelle d’ouverture est mise en surbrillance.

 Vous pouvez faire correspondre deux ou trois éléments co-occurteurs, appelés paires et triples. Les triples sont des ensembles de trois éléments co-occurants. Par exemple, dans le `foreach` C, l’énoncé forme un triple : `foreach()`, `{`et `}`. Les trois éléments sont mis en évidence lorsque l’attelle de fermeture est tapée.

 Les services linguistiques hérités sont mis en œuvre dans le cadre d’un VSPackage, mais la nouvelle façon de mettre en œuvre des fonctionnalités de service linguistique est d’utiliser des extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter l’appariement des [accolades, voir Walkthrough: Display accolades assorties](../../extensibility/walkthrough-displaying-matching-braces.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorera les performances de votre service linguistique et vous permettra de profiter des nouvelles fonctionnalités de l’éditeur.

 La <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe prend en charge <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> les <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> paires et les triples avec les méthodes et les méthodes.

## <a name="implementation"></a>Implémentation
 Le service linguistique doit identifier tous les éléments appariés dans la langue, puis localiser toutes les paires correspondantes. Ceci est généralement accompli <xref:Microsoft.VisualStudio.Package.IScanner> en mettant en œuvre pour détecter une langue assortie, puis en utilisant la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode pour correspondre aux éléments.

 La <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> méthode appelle le scanner pour symboliquer la ligne et retourner le jeton juste avant le caret. Le scanner indique qu’une paire d’éléments de langue <xref:Microsoft.VisualStudio.Package.TokenTriggers> a été trouvée en définissant une valeur de déclenchement symbolique du jeton sur le jeton actuel. La <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> méthode <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> appelle la méthode <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> qui à son tour appelle <xref:Microsoft.VisualStudio.Package.ParseReason> la méthode avec la valeur de raison d’analyse de localiser l’élément de langage correspondant. Lorsque l’élément de langage correspondant est trouvé, les deux éléments sont mis en évidence.

 Pour une description complète de la façon dont taper une attelle déclenche la mise en évidence de l’accolade, voir la section *d’opération d’analyse d’exemple* dans l’article [Legacy language service parser et scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

## <a name="enable-support-for-brace-matching"></a>Activer le support pour l’appariement d’accolade
 L’attribut <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> peut définir les entrées de registre **MatchBraces,** **MatchBracesAtCaret**et **ShowMatchingBrace** qui fixent les propriétés correspondantes de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. Les propriétés de préférence linguistique peuvent également être définies par l’utilisateur.

|Entrée de Registre|Propriété|Description|
|--------------------|--------------|-----------------|
|MatchBraces (en anglais)|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Permet l’appariement des accolades.|
|MatchBracesAtCaret|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Permet l’appariement de l’accolade au fur et à mesure que le caret se déplace.|
|ShowMatchingBrace|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Met en surbrillance l'accolade correspondante.|

## <a name="match-conditional-statements"></a>Correspondance des déclarations conditionnelles
 Vous pouvez faire correspondre `if`les `else if`déclarations conditionnelles, telles que `else`, , et , ou `#if` `#elif`, , `#else`, `#endif`de la même manière que l’appariement des délimitants. Vous pouvez sous-classer la <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe et fournir une méthode qui peut ajouter des travées de texte ainsi que des délimitants à la gamme interne d’éléments correspondants.

## <a name="set-the-trigger"></a>Réglez la gâchette
 L’exemple suivant montre comment détecter les parenthèses assorties, les accolades bouclées et les accolades carrées, et le réglage de la gâchette pour elle dans le scanner. La <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> méthode <xref:Microsoft.VisualStudio.Package.Source> sur la classe détecte la gâchette et appelle le parseur pour trouver la paire correspondante (voir la section Trouver la section *de match* dans cet article). Cet exemple n’est qu’à des fins illustratives. Il suppose que votre scanner `GetNextToken` contient une méthode qui identifie et renvoie les jetons à partir d’une ligne de texte.

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

## <a name="match-the-braces"></a>Assortir les accolades
 Voici un exemple simplifié pour `{ }`faire `( )`correspondre `[ ]`les éléments de langage, et , et en ajoutant leurs travées à l’objet. <xref:Microsoft.VisualStudio.Package.AuthoringSink> Cette approche n’est pas une approche recommandée pour analyser le code source; c’est uniquement à des fins d’illustration.

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
- [Caractéristiques du service linguistique hérité](../../extensibility/internals/legacy-language-service-features1.md)
- [Analyse et scanner de service linguistique hérité](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
