---
title: "Informations sur les paramètres dans un Service2 de langage hérité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4d806c48cd96c93774b77363f1d427968613e60b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informations sur les paramètres dans un Service de langage hérité
Informations sur les paramètres IntelliSense est une info-bulle qui affiche la signature d’une méthode lorsque l’utilisateur tape la liste de paramètres Démarrer caractère (en règle générale, une parenthèse ouvrante) pour la liste de paramètres de méthode. L’entrée de chaque paramètre et le type est le séparateur de paramètre (en général une virgule), l’info-bulle est mis à jour pour afficher le paramètre suivant en gras.  
  
 Les classes de framework (MPF) package managé prennent en charge la gestion de l’info-bulle d’informations sur les paramètres. L’analyseur doit détecter paramètre paramètre de démarrage, ensuite, et les caractères de fin de paramètre et il doivent fournir une liste des signatures de méthode et les paramètres associés.  
  
 Les services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour plus d’informations, consultez [étendre l’éditeur et les Services de langage](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## <a name="implementation"></a>Implémentation  
 L’analyseur doit définir la valeur de déclencheur <xref:Microsoft.VisualStudio.Package.TokenTriggers> est définie lorsqu’il trouve un caractère de début de la liste paramètre (souvent une parenthèse ouvrante). Il doit définir un <xref:Microsoft.VisualStudio.Package.TokenTriggers> déclencher lorsqu’il détecte un séparateur de paramètre (souvent une virgule). Cela provoque une info-bulle d’informations sur les paramètres être mis à jour et afficher le paramètre suivant en gras. L’analyseur doit définir la valeur de déclencheur <xref:Microsoft.VisualStudio.Package.TokenTriggers> lorsque si trouve le caractère de fin de liste de paramètre (souvent une parenthèse fermante).  
  
 Le <xref:Microsoft.VisualStudio.Package.TokenTriggers> déclencheur valeur lance un appel à la <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> (méthode), qui à son tour appelle la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Analyseur de méthode avec la raison de l’analyse <xref:Microsoft.VisualStudio.Package.ParseReason>. Si l’analyseur détermine que l’identificateur avant le caractère de début de la liste de paramètres est un nom de méthode reconnue, elle retourne une liste de mise en correspondance des signatures de méthode dans le <xref:Microsoft.VisualStudio.Package.AuthoringScope> objet. Si les signatures de méthode est trouvées, l’info-bulle d’informations sur les paramètres s’affiche avec la première signature dans la liste. Cette info-bulle est ensuite mis à jour plus de la signature est tapée. Lorsque le caractère de fin de liste de paramètre est de type, l’info-bulle d’informations sur les paramètres est supprimé de la vue.  
  
> [!NOTE]
>  Pour garantir que l’info-bulle d’informations sur les paramètres est correct, vous devez substituer les propriétés sur la <xref:Microsoft.VisualStudio.Package.Methods> classe pour fournir les caractères appropriés. La base de <xref:Microsoft.VisualStudio.Package.Methods> suppose de classe c#-signature de méthode de style. Consultez la <xref:Microsoft.VisualStudio.Package.Methods> classe pour plus d’informations sur la manière dont cela est possible.  
  
## <a name="enabling-support-for-the-parameter-info"></a>L’activation de la prise en charge pour les informations de paramètre  
 Pour prendre en charge les info-bulles d’informations sur les paramètres, vous devez définir le `ShowCompletion` nommé de paramètre de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> à `true`. Le service de langage lit la valeur de cette entrée de Registre à partir de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> propriété.  
  
 En outre, le <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> propriété doit être définie sur `true` pour l’info-bulle d’informations sur les paramètres à afficher.  
  
### <a name="example"></a>Exemple  
 Voici un exemple simplifié de détecter les caractères de la liste des paramètres et en définissant les déclencheurs appropriés. Cet exemple est à titre d’illustration uniquement. Il suppose que votre scanneur contient une méthode `GetNextToken` qui identifie et retourne les jetons à partir d’une ligne de texte. L’exemple de code définit simplement les déclencheurs lorsqu’il détecte le type de caractère correct.  
  
```csharp  
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
  
## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Prise en charge de l’info-bulle des informations de paramètre dans l’analyseur  
 Le <xref:Microsoft.VisualStudio.Package.Source> classe fait des hypothèses sur le contenu de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> et <xref:Microsoft.VisualStudio.Package.AuthoringSink> lorsque l’info-bulle d’informations sur les paramètres s’affiche et est mis à jour des classes.  
  
-   La fonction de l’analyseur <xref:Microsoft.VisualStudio.Package.ParseReason> quand le caractère de début de liste de paramètre est tapé.  
  
-   L’emplacement donné le <xref:Microsoft.VisualStudio.Package.ParseRequest> objet est immédiatement après le caractère de début de la liste de paramètres. L’analyseur doit collecter les signatures de toutes les déclarations de méthode disponibles à positionnement et de les stocker dans une liste dans votre version de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> objet. Cette liste inclut le nom de la méthode, type (méthode) (ou type de retour) et une liste de paramètres possibles. Cette liste est recherchée ultérieurement la signature de méthode ou des signatures à afficher dans l’info-bulle d’informations sur les paramètres.  
  
 L’analyseur doit analyser ensuite la ligne spécifiée par la <xref:Microsoft.VisualStudio.Package.ParseRequest> objet pour rassembler le nom de la méthode d’entrée, ainsi que la distance le long de l’utilisateur est en tapant les paramètres. Cela est accompli en passant le nom de la méthode à la <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> méthode sur le <xref:Microsoft.VisualStudio.Package.AuthoringSink> objet, puis en appelant le <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> méthode lorsque le caractère de début de la liste de paramètres est analysé, l’appel le <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> (méthode) lors de la liste de paramètres caractère suivant est analysé et enfin appelant le <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> méthode lorsque le caractère de fin de liste de paramètre est analysé. Les résultats de ces appels de méthode sont utilisés par la <xref:Microsoft.VisualStudio.Package.Source> classe pour mettre à jour l’info-bulle d’informations sur les paramètres de manière appropriée.  
  
### <a name="example"></a>Exemple  
 Voici une ligne de texte, que l’utilisateur peut entrer. Les nombres sous la ligne indiquent quelle étape est effectuée par l’analyseur à cette position dans la ligne (en supposant que l’analyse se déplace de gauche à droite). L’hypothèse est que toutes les modifications avant la ligne a déjà été analysée pour les signatures de méthode, y compris la signature de méthode « testfunc ».  
  
```  
testfunc("a string",3);  
     ^^          ^ ^  
     12          3 4  
```  
  
 Les étapes que l’analyseur prend sont décrites ci-dessous :  
  
1.  Les appels de l’analyseur <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> avec le texte « testfunc ».  
  
2.  Les appels de l’analyseur <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>.  
  
3.  Les appels de l’analyseur <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>.  
  
4.  Les appels de l’analyseur <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>.