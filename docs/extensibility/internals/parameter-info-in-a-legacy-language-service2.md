---
title: "Informations sur les param&#232;tres dans un Service2 de langage h&#233;rit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense, info-bulle d’informations sur les paramètres"
  - "services de langage (framework package managé), informations sur les paramètres IntelliSense"
  - "Informations sur les paramètres (IntelliSense), prise en charge dans les services de langage (framework package managé)"
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Informations sur les param&#232;tres dans un Service de langage h&#233;rit&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Informations sur les paramètres IntelliSense est une info\-bulle qui affiche la signature d’une méthode lorsque l’utilisateur tape la liste des paramètres Démarrer caractère \(généralement une parenthèse ouvrante\) pour la liste de paramètres de méthode. L’entrée de chaque paramètre et le type est le séparateur de paramètres \(en général une virgule\), l’info\-bulle est mis à jour pour afficher le paramètre suivant en gras.  
  
 Les classes du framework \(MPF\) package managé prennent en charge la gestion de l’info\-bulle d’informations sur les paramètres. L’analyseur doit détecter paramètre paramètre de démarrage, ensuite, et les caractères de fin de paramètre et il doivent fournir une liste des signatures de méthode et les paramètres associés.  
  
 Les services de langage ancien sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus, consultez [Extension de l’éditeur et les Services de langage](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## Implémentation  
 L’analyseur doit définir la valeur du déclencheur <xref:Microsoft.VisualStudio.Package.TokenTriggers> a la valeur lorsqu’elle trouve un caractère de début de la liste paramètre \(souvent une parenthèse ouvrante\). Il doit définir un <xref:Microsoft.VisualStudio.Package.TokenTriggers> déclencher lorsqu’il détecte un séparateur de paramètre \(souvent une virgule\). Ainsi, une info\-bulle d’informations sur les paramètres à jour et afficher le paramètre suivant en gras. L’analyseur doit définir la valeur du déclencheur <xref:Microsoft.VisualStudio.Package.TokenTriggers> lorsque si trouve le caractère de fin de liste paramètre \(souvent une parenthèse fermante\).  
  
 Le <xref:Microsoft.VisualStudio.Package.TokenTriggers> valeur du déclencheur lance un appel à la <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> méthode, qui à son tour appelle la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Analyseur de méthode et la raison de l’analyse <xref:Microsoft.VisualStudio.Package.ParseReason>. Si l’analyseur détermine que l’identificateur avant le caractère de début de la liste de paramètres est un nom de méthode reconnue, elle retourne une liste de faire correspondre les signatures de méthode dans le <xref:Microsoft.VisualStudio.Package.AuthoringScope> objet. Si les signatures de méthode est trouvées, l’info\-bulle d’informations sur les paramètres s’affiche avec la première signature dans la liste. Cette info\-bulle est ensuite mis à jour de la signature est tapée. Lorsque le caractère de fin de liste de paramètre est de type, l’info\-bulle d’informations sur les paramètres est supprimé de la vue.  
  
> [!NOTE]
>  Pour vous assurer que l’info\-bulle d’informations sur les paramètres n’est pas formaté correctement, vous devez substituer les propriétés sur la <xref:Microsoft.VisualStudio.Package.Methods> classe pour fournir les caractères appropriés. La base de <xref:Microsoft.VisualStudio.Package.Methods> suppose de classe c\#\-signature de méthode de style. Consultez la <xref:Microsoft.VisualStudio.Package.Methods> classe pour plus d’informations sur la façon dont cela est possible.  
  
## Prise en charge pour les informations de paramètre  
 Pour prendre en charge les info\-bulles d’informations sur les paramètres, vous devez définir la `ShowCompletion` nommé du paramètre de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> à `true`. Le service de langage lit la valeur de cette entrée de Registre à partir de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> propriété.  
  
 En outre, le <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> propriété doit être définie sur `true` pour l’info\-bulle d’informations sur les paramètres à afficher.  
  
### Exemple  
 Voici un exemple simplifié de détecter les caractères de la liste des paramètres et en définissant les déclencheurs appropriés. Cet exemple est à titre indicatif uniquement. Il part du principe que votre scanneur contient une méthode `GetNextToken` qui identifie et retourne des jetons à partir d’une ligne de texte. L’exemple de code définit simplement les déclencheurs lorsqu’il détecte le type de caractère correct.  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private Lexer lex;  
        private const char parameterListStartChar = '(';  
        private const char parameterListEndChar   = ')';  
        private const char parameterNextChar      = ',';  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char c = token[0];  
                if (Char.IsPunctuation(c))  
                {  
                    tokenInfo.Type = TokenType.Operator;  
                    tokenInfo.Color = TokenColor.Keyword;  
                    tokenInfo.EndIndex = index;  
  
                    if (c == parameterListStartChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterStart;  
                    }  
                    else if (c == parameterListNextChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterNext;  
                    else if (c == parameterListEndChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterEnd;  
                    }  
                }  
            return foundToken;  
        }  
    }  
}  
```  
  
## Prise en charge de l’info\-bulle d’informations de paramètre dans l’analyseur  
 La <xref:Microsoft.VisualStudio.Package.Source> classe fait des hypothèses sur le contenu de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> et <xref:Microsoft.VisualStudio.Package.AuthoringSink> lorsque l’info\-bulle d’informations sur les paramètres est affichée et mise à jour des classes.  
  
-   L’analyseur est donné <xref:Microsoft.VisualStudio.Package.ParseReason> lorsque le caractère de début de liste de paramètre est typé.  
  
-   L’emplacement indiqué dans le <xref:Microsoft.VisualStudio.Package.ParseRequest> objet est immédiatement après le caractère de début de la liste de paramètres. L’analyseur doit collecter les signatures de toutes les déclarations de méthode disponibles à positionnement et de les stocker dans une liste dans votre version de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> objet. Cette liste inclut le nom de la méthode, type \(méthode\) \(ou type de retour\) et une liste de paramètres possibles. Cette liste est recherchée ultérieurement pour la signature de méthode ou des signatures à afficher dans l’info\-bulle d’informations sur les paramètres.  
  
 L’analyseur doit analyser ensuite la ligne spécifiée par la <xref:Microsoft.VisualStudio.Package.ParseRequest> objet pour rassembler le nom de la méthode d’entrée, ainsi que sur l’utilisateur est en tapant. Cela en transmettant le nom de la méthode à la <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> méthode sur le <xref:Microsoft.VisualStudio.Package.AuthoringSink> objet, puis en appelant le <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> méthode lorsque le caractère de début de la liste de paramètres est analysé, l’appel la <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> méthode lorsque le caractère suivant de liste de paramètre est analysé et enfin appeler le <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> méthode lorsque le caractère de fin de liste de paramètre est analysé. Les résultats de ces appels de méthode sont utilisés par la <xref:Microsoft.VisualStudio.Package.Source> classe mise à jour de manière appropriée l’info\-bulle d’informations sur les paramètres.  
  
### Exemple  
 Voici une ligne de texte que l’utilisateur peut entrer. Les nombres en dessous de la ligne indiquent quelle action est effectuée par l’analyseur à cet emplacement dans la ligne \(en supposant que l’analyse se déplace de gauche à droite\). L’hypothèse est que tout ce qui précède la ligne a déjà été analysé pour les signatures de méthode, y compris la signature de méthode « testfunc ».  
  
```  
testfunc("a string",3);  
     ^^          ^ ^  
     12          3 4  
```  
  
 Les étapes qui prend l’analyseur sont décrites ci\-dessous :  
  
1.  Les appels de l’analyseur <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> avec le texte « testfunc ».  
  
2.  Les appels de l’analyseur <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>.  
  
3.  Les appels de l’analyseur <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>.  
  
4.  Les appels de l’analyseur <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>.