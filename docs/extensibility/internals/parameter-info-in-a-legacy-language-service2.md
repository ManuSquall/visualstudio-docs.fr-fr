---
title: Informations sur les paramètres dans un langage hérité Service2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dff6e871320d0727ed2fbec4188e8f7af2e5c5fe
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "88237956"
---
# <a name="parameter-info-in-a-legacy-language-service-2"></a>Informations sur les paramètres dans un service de langage hérité 2
Infos sur les paramètres IntelliSense est une info-bulle qui affiche la signature d’une méthode lorsque l’utilisateur tape le caractère de début de la liste de paramètres (généralement une parenthèse ouvrante) pour la liste des paramètres de la méthode. À mesure que chaque paramètre est entré et que le séparateur de paramètres (généralement une virgule) est tapé, l’info-bulle est mise à jour pour afficher le paramètre suivant en gras.

 Les classes MPF (Managed package Framework) prennent en charge la gestion de l’info-bulle informations sur les paramètres. L’analyseur doit détecter les caractères de début, de paramètre et de fin de paramètre, et il doit fournir une liste des signatures de méthode et leurs paramètres associés.

 Les services de langage hérités sont implémentés dans le cadre d’un VSPackage, mais la meilleure façon d’implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus, consultez [extension de l’éditeur et des services de langage](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser la nouvelle API Editor dès que possible. Cela améliore les performances de votre service de langage et vous permet de tirer parti des nouvelles fonctionnalités de l’éditeur.

## <a name="implementation"></a>Implémentation
 L’analyseur doit définir la valeur du déclencheur <xref:Microsoft.VisualStudio.Package.TokenTriggers> lorsqu’il trouve un caractère de début de liste de paramètres (souvent une parenthèse ouvrante). Il doit définir un <xref:Microsoft.VisualStudio.Package.TokenTriggers> déclencheur lorsqu’il trouve un séparateur de paramètres (souvent une virgule). Cela entraîne la mise à jour d’une info-bulle d’informations sur les paramètres et affiche le paramètre suivant en gras. L’analyseur doit définir la valeur du déclencheur <xref:Microsoft.VisualStudio.Package.TokenTriggers> si recherche le caractère de fin de liste de paramètres (souvent une parenthèse fermante).

 La <xref:Microsoft.VisualStudio.Package.TokenTriggers> valeur du déclencheur lance un appel à la <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> méthode, qui à son tour appelle l' <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Analyseur de méthode avec une raison d’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason> . Si l’analyseur détermine que l’identificateur avant le caractère de début de liste de paramètres est un nom de méthode reconnu, il retourne une liste de signatures de méthode correspondantes dans l' <xref:Microsoft.VisualStudio.Package.AuthoringScope> objet. Si des signatures de méthode ont été trouvées, l’info-bulle informations sur les paramètres s’affiche avec la première signature dans la liste. Cette info-bulle est ensuite mise à jour au fur et à mesure que la signature est tapée. Lorsque le caractère de fin de la liste de paramètres est tapé, l’info-bulle des informations sur les paramètres est supprimée de l’affichage.

> [!NOTE]
> Pour vous assurer que l’info-bulle informations sur les paramètres est correctement mise en forme, vous devez substituer les propriétés de la <xref:Microsoft.VisualStudio.Package.Methods> classe pour fournir les caractères appropriés. La classe de base <xref:Microsoft.VisualStudio.Package.Methods> suppose une signature de méthode de style C#. <xref:Microsoft.VisualStudio.Package.Methods>Pour plus d’informations sur la façon de procéder, consultez la classe.

## <a name="enabling-support-for-the-parameter-info"></a>Activation de la prise en charge des informations sur les paramètres
 Pour prendre en charge les info-bulles d’informations sur les paramètres, vous devez définir le `ShowCompletion` paramètre nommé de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> valeur sur `true` . Le service de langage lit la valeur de cette entrée de Registre à partir de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> propriété.

 En outre, la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> propriété doit avoir la valeur `true` pour que l’info-bulle informations sur les paramètres s’affiche.

### <a name="example"></a>Exemple
 Voici un exemple simplifié de détection des caractères de la liste de paramètres et de la définition des déclencheurs appropriés. Cet exemple est fourni à titre d’illustration uniquement. Elle suppose que votre scanneur contient une méthode `GetNextToken` qui identifie et retourne des jetons à partir d’une ligne de texte. L’exemple de code définit simplement les déclencheurs chaque fois qu’il voit le type de caractère approprié.

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

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Prise en charge de l’info-bulle info sur les paramètres dans l’analyseur
 La <xref:Microsoft.VisualStudio.Package.Source> classe fait des suppositions sur le contenu des <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.AuthoringSink> classes et lorsque l’info-bulle info sur les paramètres est affichée et mise à jour.

- L’analyseur est fourni <xref:Microsoft.VisualStudio.Package.ParseReason> lorsque le caractère de début de la liste de paramètres est tapé.

- L’emplacement donné dans l' <xref:Microsoft.VisualStudio.Package.ParseRequest> objet est immédiatement après le caractère de début de la liste de paramètres. L’analyseur doit collecter les signatures de toutes les déclarations de méthode disponibles à cette position et les stocker dans une liste dans votre version de l' <xref:Microsoft.VisualStudio.Package.AuthoringScope> objet. Cette liste comprend le nom de la méthode, le type de méthode (ou le type de retour) et une liste de paramètres possibles. Cette liste est ensuite recherchée dans la signature de la méthode ou les signatures à afficher dans l’info-bulle des informations sur les paramètres.

  L’analyseur doit ensuite analyser la ligne spécifiée par l' <xref:Microsoft.VisualStudio.Package.ParseRequest> objet pour rassembler le nom de la méthode en cours d’entrée, ainsi que la façon dont l’utilisateur se trouve dans les paramètres de saisie. Pour ce faire, vous devez passer le nom de la méthode à la <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> méthode sur l' <xref:Microsoft.VisualStudio.Package.AuthoringSink> objet, puis appeler la <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> méthode lorsque le caractère de début de la liste de paramètres est analysé, en appelant la <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> méthode lorsque le caractère suivant de la liste de paramètres est analysé, et enfin en appelant la <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> méthode lorsque le caractère de fin de la liste de paramètres est analysé. Les résultats de ces appels de méthode sont utilisés par la <xref:Microsoft.VisualStudio.Package.Source> classe pour mettre à jour l’info-bulle d’informations de paramètre de manière appropriée.

### <a name="example"></a>Exemple
 Voici une ligne de texte que l’utilisateur peut entrer. Les nombres sous la ligne indiquent quelle étape est effectuée par l’analyseur à cette position dans la ligne (en supposant que l’analyse se déplace de gauche à droite). L’hypothèse est que tout ce qui précède la ligne a déjà été analysé pour les signatures de méthode, y compris la signature de la méthode « TestFunc ».

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 Les étapes que prend l’analyseur sont décrites ci-dessous :

1. L’analyseur appelle <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> avec le texte « TestFunc ».

2. L’analyseur appelle <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> .

3. L’analyseur appelle <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> .

4. L’analyseur appelle <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> .
