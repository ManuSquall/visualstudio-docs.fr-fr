---
title: Utiliser les expressions régulières
description: Découvrez certains caractères d’expression régulière, les opérateurs, les constructions et les exemples de modèles que vous pouvez utiliser dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/13/2019
ms.topic: conceptual
f1_keywords:
- vsregularexpressionhelp
- vs.regularexpressionhelp
- vs.wildcardsbuilder
- vs.netregularexpressionhelp
- vs.wildcards
helpviewer_keywords:
- regular expressions [Visual Studio]
- regular expressions
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d62d35a296c70462aab75af5a8c6729179d5b34d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925772"
---
# <a name="use-regular-expressions-in-visual-studio"></a>Utiliser des expressions régulières dans Visual Studio

Visual Studio utilise des [expressions régulières de .NET](/dotnet/standard/base-types/regular-expressions) pour rechercher et remplacer du texte.

## <a name="regular-expression-examples"></a>Exemples d’expressions régulières

Le tableau suivant contient des caractères, des opérateurs, des constructions et des exemples de modèles relatifs aux expressions régulières. Pour obtenir une référence plus complète, consultez [Langage des expressions régulières](/dotnet/standard/base-types/regular-expression-language-quick-reference).

|Objectif|Expression|Exemple|
|-------------|----------------|-------------|
|Correspond à n'importe quel caractère unique (sauf un saut de ligne). Pour plus d’informations, consultez [N’importe quel caractère](/dotnet/standard/base-types/character-classes-in-regular-expressions#any-character-).|.|`a.o` met en correspondance « Tao » dans « autour de » et « ABO » dans « about », mais pas « Acro » dans « sur »|
|Correspond à zéro ou plusieurs occurrences de l'expression précédente (correspond à autant de caractères que possible). Pour plus d’informations, consultez [Mettre en correspondance zéro occurrence ou plus](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-).|*|`a*r` correspond à "r" dans "rack", à "rar" dans "ark" et à "aar" dans "aardvark"|
|Correspond à n’importe quel caractère zéro ou plusieurs fois.|.*|`c.*e` correspond à « cke » dans « racket », à « comme » dans « commentaire » et à « code » dans « code ».|
|Correspond à une ou plusieurs occurrences de l'expression précédente (correspond à autant de caractères que possible). Pour plus d’informations, consultez [Mettre en correspondance une occurrence ou plus](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-).|+|`e+d` correspond à « seau » dans « Feeder » et « Ed » dans « Terni »|
|Faire correspondre à n'importe quel caractère une ou plusieurs fois.|.+|`e.+e` correspond à « EEDE » dans « Feeder », mais ne trouve pas de correspondance dans « feed »|
|Correspond à zéro ou plusieurs occurrences de l'expression précédente (correspond au minimum de caractères possible). Pour plus d’informations, consultez [Mettre en correspondance zéro occurrence ou plus (correspondance paresseuse)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-lazy-match-).|*?|`\w*?d` correspond à « FAD » et « Ed » dans « Terni », mais pas au mot entier « Terni » en raison de la correspondance tardive|
|Correspond à une ou plusieurs occurrences de l'expression précédente (correspond au minimum de caractères possible). Pour plus d’informations, consultez [Mettre en correspondance une occurrence ou plus (correspondance paresseuse)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-lazy-match-).|+?|`e\w+?` correspond à « EE » dans « en veille » et à « Ed » dans « Terni », mais ne trouve aucune correspondance dans « fondu »|
|Ancre la chaîne de correspondance [au début d'une ligne ou d'une chaîne](/dotnet/standard/base-types/anchors-in-regular-expressions#start-of-string-or-line-)|^|`^car` correspond au mot « car » uniquement lorsqu’il apparaît au début d’une ligne|
|Ancre la chaîne de correspondance à la [fin d'une ligne](/dotnet/standard/base-types/anchors-in-regular-expressions#end-of-string-or-line-)|\r?$|`car\r?$` correspond à « car » uniquement lorsqu’il apparaît à la fin d’une ligne|
|Ancre la chaîne de correspondance à la fin du fichier|$|`car$` correspond à « car » uniquement lorsqu’il apparaît à la fin du fichier|
|Correspond à n'importe quel caractère unique d'un ensemble|[abc]|`b[abc]` correspond à « BA », « BB » et « BC »|
|Correspond à n'importe quel caractère dans une plage de caractères|[a-f]|`be[n-t]` correspond à « Bet » dans « between », « Ben » dans « sous » et « BES » dans « beside », mais ne trouve aucune correspondance dans « ci-dessous »|
|Capture et numérote implicitement l'expression contenue dans les parenthèses|()|`([a-z])X\1` correspond à "aXa" et à "bXb", mais pas à "aXb". « \1 » fait référence au premier groupe d’expressions « [a-z] ». Pour plus d’informations, consultez [Groupes de capture et modèles de remplacement](#capture-groups-and-replacement-patterns). |
|Invalide une correspondance|(?!abc)|`real(?!ity)` correspond à "real" dans "realty" et dans "really", mais pas dans "reality". Trouve également le deuxième « real » (mais pas le premier « real ») dans « realityreal ».|
|Correspond à n'importe quel caractère qui ne figure pas dans un ensemble donné de caractères. Pour plus d’informations, consultez [Groupe de caractères négatif](/dotnet/standard/base-types/character-classes-in-regular-expressions#negative-character-group-).|[^abc]|`be[^n-t]` correspond à « BEF » dans « Before », à « BA » dans « behind » et à « Bel » dans « ci-dessous », mais ne trouve pas de correspondance dans « sous »|
|Correspond à l'expression placée avant ou après le symbole|&#124;|`(sponge|mud) bath` correspond à « éponge bain » et à « bain de boue »|
|[Crée une séquence d'échappement](/dotnet/standard/base-types/character-escapes-in-regular-expressions) pour le caractère placé après la barre oblique inverse| \\ |`\^` correspond au caractère ^|
|Spécifie le nombre d'occurrences du caractère ou du groupe précédent. Pour plus d’informations, consultez [Mettre en correspondance exactement n occurrences](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-exactly-n-times-n).|{n}, où n est le nombre d'occurrences|`x(ab){2}x` correspond à « xababx »<br/>`x(ab){2,3}x` correspond à « xababx » et à « xabababx », mais pas à « xababababx »|
|[Mettre en correspondance un texte dans une catégorie Unicode](/dotnet/standard/base-types/character-classes-in-regular-expressions#unicode-category-or-unicode-block-p). Pour plus d’informations sur les classes de caractères Unicode, consultez [Propriétés des caractères de la norme Unicode 5.2](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf).|\p{X}, où "X" est le numéro Unicode.|`\p{Lu}` correspond à « T » et « D » dans « Thomas Doe »|
|[Correspond à une limite de mot](/dotnet/standard/base-types/anchors-in-regular-expressions#word-boundary-b)|\b (en dehors d’une classe de caractères `\b` spécifie une limite de mot et, à l’intérieur d’une classe de caractères, `\b` spécifie un retour arrière)|`\bin` correspond à « in » dans « à l’intérieur de », mais ne trouve pas de correspondance dans « Pinto »|
|Correspond à un saut de ligne (c’est-à-dire un retour chariot suivi d’une nouvelle ligne)|\r?\n|`End\r?\nBegin` correspond à "End" et "Begin" uniquement lorsque "End" est la dernière chaîne d’une ligne et "Begin" est la première chaîne de la ligne suivante|
|Mettre en correspondance avec n’importe quel [caractère alphabétique](/dotnet/standard/base-types/character-classes-in-regular-expressions#word-character-w)|\w|`a\wd` correspond à « Add » et à « A1D », mais pas à « a d »|
|Correspond à n'importe quel [espace blanc](/dotnet/standard/base-types/character-classes-in-regular-expressions#whitespace-character-s)|\s|`Public\sInterface` correspond à l’expression « public interface »|
|Mettre en correspondance avec n’importe quel [caractère numérique décimal](/dotnet/standard/base-types/character-classes-in-regular-expressions#decimal-digit-character-d)|\d|`\d` correspond à « 4 » et « 0 » dans « WD40 »|

Un exemple d’expression régulière qui combine certains des opérateurs et des constructions pour correspondre à un nombre hexadécimal est `\b0[xX]([0-9a-fA-F]+\)\b` . Cette expression correspond à « 0xc67f », mais pas à « 0xc67g ».

> [!TIP]
> Dans les systèmes d’exploitation Windows, la plupart des lignes se terminent par « \r\n » (retour chariot suivi d’une nouvelle ligne). Ces caractères ne sont pas visibles, mais sont présents dans l’éditeur et transmis au service d’expression régulière .NET.

## <a name="capture-groups-and-replacement-patterns"></a>Groupes de capture et modèles de remplacement

Un groupe de capture délimite une sous-expression d’une expression régulière et capture une sous-chaîne d’une chaîne d’entrée. Vous pouvez utiliser les groupes de capture dans l’expression régulière elle-même (par exemple pour rechercher un mot en double), ou dans un modèle de remplacement. Pour plus d’informations, consultez [Constructions de regroupement dans les expressions régulières](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions).

Pour créer un groupe de capture numéroté, placez la sous-expression entre parenthèses dans le modèle d’expression régulière. Les captures sont numérotées automatiquement de la gauche vers la droite en fonction de l'ordre des parenthèses ouvrantes dans l'expression régulière. Pour accéder au groupe capturé :

- **dans l’expression régulière**: utilisez `\number` . Par exemple, `\1` dans l’expression régulière `(\w+)\s\1` fait référence au premier groupe de capture `(\w+)`.

- **dans un modèle de remplacement**: utilisez `$number` . Par exemple, l’expression régulière groupée `(\d)([a-z])` définit deux groupes : le premier contient un chiffre décimal unique tandis que le deuxième contient un caractère unique compris entre **a** et **z**. L’expression recherche quatre correspondances dans la chaîne suivante : **1a 2b 3c 4d**. La chaîne de remplacement `z$1` référence le premier groupe uniquement (`$1`) et convertit la chaîne en **z1 z2 z3 z4**.

L’illustration suivante montre une expression régulière `(\w+)\s\1` et une chaîne de remplacement `$1`. L’expression régulière et le modèle de remplacement font référence au premier groupe de capture qui a reçoit automatiquement le numéro 1. Lorsque vous choisissez **Remplacer tout** dans la boîte de dialogue **Remplacement rapide** de Visual Studio, les mots répétés sont supprimés du texte.

![Remplacement rapide montrant un groupe de capture numéroté dans Visual Studio](media/numbered-capture-group.png)

> [!TIP]
> Assurez-vous que le bouton **Utiliser des expressions régulières** est sélectionné dans la boîte de dialogue **Remplacement rapide**.

### <a name="named-capture-groups"></a>Groupes de capture nommés

Au lieu d’utiliser la numérotation automatique d’un groupe de capture, vous pouvez lui donner un nom. La syntaxe pour un groupe de capture nommé est `(?<name>subexpression)`.

Les groupes de capture nommés, tout comme les groupes numérotés, peuvent être utilisés dans l’expression régulière elle-même ou dans un modèle de remplacement. Pour accéder au groupe de capture nommé :

- **dans l’expression régulière**: utilisez `\k<name>` . Par exemple, `\k<repeated>` dans l’expression régulière `(?<repeated>\w+)\s\k<repeated>` fait référence au groupe de capture nommé `repeated` et dont la sous-expression est `\w+`.

- **dans un modèle de remplacement**: utilisez `${name}` . Par exemple : `${repeated}`.

Par exemple, l’illustration suivante montre une expression régulière `(?<repeated>\w+)\s\k<repeated>` et une chaîne de remplacement `${repeated}`. L’expression régulière et le modèle de remplacement font référence au groupe de capture nommé `repeated`. Lorsque vous choisissez **Remplacer tout** dans la boîte de dialogue **Remplacement rapide** de Visual Studio, les mots répétés sont supprimés du texte.

![Remplacement rapide montrant un groupe de capture nommé dans Visual Studio](media/named-capture-group.png)

> [!TIP]
> Assurez-vous que le bouton **Utiliser des expressions régulières** est sélectionné dans la boîte de dialogue **Remplacement rapide**.

Pour plus d'informations sur les groupes de capture nommés, voir [Sous-expressions mises en correspondance nommées](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions#named-matched-subexpressions). Pour plus d’informations sur les expressions régulières utilisées dans les modèles de remplacement, consultez [Substitutions dans les expressions régulières](/dotnet/standard/base-types/substitutions-in-regular-expressions).

## <a name="see-also"></a>Voir aussi

- [Langage des expressions régulières](/dotnet/standard/base-types/regular-expression-language-quick-reference)
- [Rechercher et remplacer du texte](../ide/finding-and-replacing-text.md)
