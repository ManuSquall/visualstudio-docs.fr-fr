---
title: "Accolades correspondantes dans un Service de langage h&#233;rit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Accolades correspondantes"
  - "services de langage (framework package managé), la correspondance des accolades"
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# Accolades correspondantes dans un Service de langage h&#233;rit&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Accolades correspondantes permet le développeur à effectuer le suivi des éléments de langage qui doivent se produire ensemble, tels que des parenthèses et des accolades. Lorsqu’un développeur entre une accolade fermante, l’accolade ouvrante est mis en surbrillance.  
  
 Vous pouvez associer deux ou trois éléments qui se produisent conjointement, appelés paires et triples. Triples sont des ensembles de trois éléments qui se produisent conjointement. Par exemple, en c\#, la `foreach` instruction constitue un triple : «`foreach()`«, »`{`», et «`}`». Les trois éléments sont mis en surbrillance lorsque vous avez tapée l’accolade fermante.  
  
 Les services de langage ancien sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter les accolades correspondantes, consultez [Procédure pas à pas : Affichage des accolades correspondantes](../../extensibility/walkthrough-displaying-matching-braces.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
 La <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe prend en charge les deux paires et triple avec le <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> et <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> méthodes.  
  
## Implémentation  
 Le service de langage doit identifier tous les éléments de mise en correspondance dans la langue et recherchez toutes les paires correspondantes. Cela est généralement effectuée en implémentant <xref:Microsoft.VisualStudio.Package.IScanner> pour détecter une langue correspondante, puis l’utilisation du <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode pour faire correspondre les éléments.  
  
 Le <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> méthode appelle le moteur d’analyse pour marquer la ligne et retourner le jeton juste avant le signe insertion. Le moteur d’analyse indique qu’une paire d’élément de langage a été trouvée en définissant une valeur de déclencheur d’émission de jeton de <xref:Microsoft.VisualStudio.Package.TokenTriggers> du jeton actuel. Le <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> des appels de méthode du <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> méthode qui appelle à son tour la <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> méthode avec la valeur de motif de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason> pour localiser l’élément de langage correspondant. Lorsque l’élément de langage correspondant est trouvé, les deux éléments sont mis en surbrillance.  
  
 Pour obtenir une description complète de comment taper une accolade déclenche la mise en évidence des accolades, consultez la section « Exemple d’opération analyser » dans la rubrique [Scanneur et analyseur du Service de langage ancien](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
## L’activation de la prise en charge pour la correspondance des accolades  
 Le <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attribut peut définir le `MatchBraces`, `MatchBracesAtCaret`, et `ShowMatchingBrace` des paramètres nommés qui définit les propriétés correspondantes de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. Propriétés de préférence de langue peuvent également être définies par l’utilisateur.  
  
|Entrée de Registre|Propriété|Description|  
|------------------------|---------------|-----------------|  
|`MatchBraces`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Active les accolades correspondantes|  
|`MatchBracesAtCaret`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Correspondance des accolades permet que le curseur se déplace.|  
|`ShowMatchingBrace`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Met en surbrillance l’accolade correspondante.|  
  
## Mise en correspondance des instructions conditionnelles  
 Vous pouvez faire correspondre les instructions conditionnelles, telles que `if`, `else if`, et `else`, ou `#if`, `#elif`, `#else`, `#endif`, de la même façon que la correspondance des séparateurs. Vous pouvez créer une sous\-classe la <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe et fournir une méthode que vous pouvez ajouter du texte s’étend ainsi que des délimiteurs dans le tableau interne d’éléments correspondants.  
  
## Définition du déclencheur  
 L’exemple suivant montre comment détecter la correspondance des parenthèses, des accolades et crochets et définissant le déclencheur pour lui dans l’analyseur. Le <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> méthode sur la <xref:Microsoft.VisualStudio.Package.Source> classe détecte le déclencheur et appelle l’analyseur pour rechercher la paire correspondante \(voir la section « Recherche la correspondance » dans cette rubrique\). Cet exemple est à titre indicatif uniquement. Il part du principe que votre scanneur contient une méthode `GetNextToken` qui identifie et retourne des jetons à partir d’une ligne de texte.  
  
```c#  
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
  
## Les accolades correspondantes  
 Voici un exemple simplifié de correspondant à la langue, éléments {}, \(\) et \[\] et d’ajouter leurs étendues à la <xref:Microsoft.VisualStudio.Package.AuthoringSink> objet. Cette approche n’est pas une approche recommandée pour l’analyse du code source ; Il est à titre indicatif uniquement.  
  
```c#  
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
  
## Voir aussi  
 [Fonctionnalités du Service de langage ancien](../../extensibility/internals/legacy-language-service-features1.md)   
 [Scanneur et analyseur du Service de langage ancien](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)