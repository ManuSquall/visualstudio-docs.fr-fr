---
title: Informations sur les paramètres dans un service de langue héritée2 Microsoft Docs
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
ms.openlocfilehash: e2c40c9ca5c038a70714545f4133db0c0dd686d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706749"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informations sur les paramètres dans un service de langage hérité
IntelliSense Parameter Info est un outil qui affiche la signature d’une méthode lorsque l’utilisateur tape le caractère de début de liste de paramètres (généralement une parenthèse ouverte) pour la liste des paramètres de la méthode. Au fur et à mesure que chaque paramètre est entré et que le séparateur de paramètres (généralement une virgule) est tapé, l’outil est mis à jour pour afficher le paramètre suivant en gras.

 Les classes de cadre de paquets gérés (MPF) fournissent un soutien à la gestion de l’outil Paramétip Info. Le parseur doit détecter le début du paramètre, le paramètre suivant et les paramètres finaux, et il doit fournir une liste des signatures de la méthode et de leurs paramètres associés.

 Les services linguistiques hérités sont mis en œuvre dans le cadre d’un VSPackage, mais la nouvelle façon de mettre en œuvre des fonctionnalités de service linguistique est d’utiliser des extensions MEF. Pour en savoir plus, voir [Extending the Editor and Language Services](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorera les performances de votre service linguistique et vous permettra de profiter des nouvelles fonctionnalités de l’éditeur.

## <a name="implementation"></a>Implémentation
 Le parseur doit définir <xref:Microsoft.VisualStudio.Package.TokenTriggers> la valeur de déclenchement est défini lorsqu’il trouve un caractère de début de liste de paramètres (souvent une parenthèse ouverte). Il doit <xref:Microsoft.VisualStudio.Package.TokenTriggers> définir un déclencheur lorsqu’il trouve un séparateur de paramètre (souvent une virgule). Cela provoque une mise à jour d’un outil d’information paramétalité et affiche le paramètre suivant en gras. Le parseur doit définir <xref:Microsoft.VisualStudio.Package.TokenTriggers> la valeur de déclenchement lorsque, s’il trouve le caractère fin de la liste de paramètres (souvent une parenthèse proche).

 La <xref:Microsoft.VisualStudio.Package.TokenTriggers> valeur de déclenchement initie un appel à la <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> méthode, qui à son tour appelle l’analyse de méthode <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> avec une raison d’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason>. Si le parseur détermine que l’identifiant avant le nom de début de la liste de <xref:Microsoft.VisualStudio.Package.AuthoringScope> paramètres est un nom de méthode reconnu, il renvoie une liste de signatures de méthode correspondantes dans l’objet. Si des signatures de méthode ont été trouvées, l’outil Paramét info est affiché avec la première signature de la liste. Cette boîte à outils est ensuite mise à jour que plus de la signature est tapée. Lorsque le caractère final de la liste de paramètres est tapé, l’outil d’info paramètre est supprimé de la vue.

> [!NOTE]
> Pour vous assurer que l’outil d’info Paramètre est correctement <xref:Microsoft.VisualStudio.Package.Methods> formaté, vous devez remplacer les propriétés de la classe pour fournir les caractères appropriés. La <xref:Microsoft.VisualStudio.Package.Methods> classe de base assume une signature de méthode de type C. Consultez <xref:Microsoft.VisualStudio.Package.Methods> la classe pour plus de détails sur la façon dont cela peut être fait.

## <a name="enabling-support-for-the-parameter-info"></a>Permettre le support pour les informations sur les paramètres
 Pour prendre en charge les outils `ShowCompletion` d’info <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> paramètres, vous devez définir le paramètre désigné du . `true` Le service linguistique lit la valeur <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> de cette entrée de registre à partir de la propriété.

 En outre, <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> la propriété `true` doit être définie pour que l’outil d’information paramétif soit affiché.

### <a name="example"></a>Exemple
 Voici un exemple simplifié de détection des caractères de liste de paramètres et de définition des déclencheurs appropriés. Cet exemple n’est qu’à des fins illustratives. Il suppose que votre scanner `GetNextToken` contient une méthode qui identifie et renvoie les jetons à partir d’une ligne de texte. Le code d’exemple définit simplement les déclencheurs chaque fois qu’il voit le bon type de caractère.

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

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Soutenir l’outil d’information paramètreTip dans le Parser
 La <xref:Microsoft.VisualStudio.Package.Source> classe fait quelques hypothèses <xref:Microsoft.VisualStudio.Package.AuthoringScope> sur <xref:Microsoft.VisualStudio.Package.AuthoringSink> le contenu et les classes lorsque l’outil d’info paramètre est affiché et mis à jour.

- Le parseur <xref:Microsoft.VisualStudio.Package.ParseReason> est donné lorsque le caractère de démarrage de la liste de paramètres est tapé.

- L’emplacement donné <xref:Microsoft.VisualStudio.Package.ParseRequest> dans l’objet est immédiatement après le caractère de début de la liste de paramètres. Le analyseur doit recueillir les signatures de toutes les déclarations de méthode disponibles <xref:Microsoft.VisualStudio.Package.AuthoringScope> à cette position et les stocker dans une liste dans votre version de l’objet. Cette liste comprend le nom de la méthode, le type de méthode (ou le type de retour), et une liste de paramètres possibles. Cette liste est ensuite recherchée pour la signature de la méthode ou les signatures à afficher dans l’outil ParaMét.

  Le parseur doit ensuite analyser la <xref:Microsoft.VisualStudio.Package.ParseRequest> ligne spécifiée par l’objet pour recueillir le nom de la méthode saisie ainsi que la distance parcourue par l’utilisateur dans les paramètres de dactylographie. Ceci est accompli en passant le <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> nom de <xref:Microsoft.VisualStudio.Package.AuthoringSink> la méthode <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> à la méthode sur l’objet, puis <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> en appelant la méthode lorsque le caractère de <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> début de liste de paramètres est analysé, appelant la méthode lorsque la liste de paramètres suivant caractère est analysé, et enfin appeler la méthode lorsque le caractère de fin de liste de paramètres est analysé. Les résultats de ces appels <xref:Microsoft.VisualStudio.Package.Source> de méthode sont utilisés par la classe pour mettre à jour l’outil Paramètre Info de manière appropriée.

### <a name="example"></a>Exemple
 Voici une ligne de texte que l’utilisateur peut entrer. Les nombres ci-dessous la ligne indiquent quelle étape est prise par le parseur à cette position dans la ligne (en supposant que l’analyse se déplace de gauche à droite). L’hypothèse ici est que tout avant la ligne a déjà été analysé pour les signatures de méthode, y compris la signature de la méthode "testfunc".

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 Les étapes que prend le parseur sont décrites ci-dessous :

1. Le parseur <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> appelle avec le texte "testfunc".

2. Le parser <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>appelle .

3. Le parser <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>appelle .

4. Le parser <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>appelle .
