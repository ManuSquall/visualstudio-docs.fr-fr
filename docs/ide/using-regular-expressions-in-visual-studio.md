---
title: Utiliser les expressions régulières
ms.date: 03/26/2018
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4e461fd69e048e406fbe062ff297da9baab3696
ms.sourcegitcommit: 8562a337cc9f674c756a4a0b2c7e288ebd61b51e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345745"
---
# <a name="use-regular-expressions-in-visual-studio"></a>Utiliser des expressions régulières dans Visual Studio

Visual Studio utilise des [expressions régulières de .NET](/dotnet/standard/base-types/regular-expressions) pour rechercher et remplacer du texte.

## <a name="regular-expression-examples"></a>Exemples d’expressions régulières

Le tableau suivant contient des caractères, des opérateurs, des constructions et des exemples de modèles relatifs aux expressions régulières. Pour obtenir une référence plus complète, consultez [Langage des expressions régulières](/dotnet/standard/base-types/regular-expression-language-quick-reference).

|Objectif|Expression|Exemples|
|-------------|----------------|-------------|
|Correspond à n'importe quel caractère unique (sauf un saut de ligne). Pour plus d’informations, consultez [N’importe quel caractère](/dotnet/standard/base-types/character-classes-in-regular-expressions#any-character-).|.|`a.o` correspond à "aro" dans "around" et à "abo" dans "about", mais pas à "acro" dans "across".|
|Correspond à zéro ou plusieurs occurrences de l'expression précédente (correspond à autant de caractères que possible). Pour plus d’informations, consultez [Mettre en correspondance zéro occurrence ou plus](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-).|*|`a*r` correspond à "r" dans "rack", à "rar" dans "ark" et à "aar" dans "aardvark"|
|Correspond à n’importe quel caractère zéro ou plusieurs fois (caractère générique \*)|.*|`c.*e` correspond à « cke » dans « racket », à « comme » dans « commentaire » et à « code » dans « code ».|
|Correspond à une ou plusieurs occurrences de l'expression précédente (correspond à autant de caractères que possible). Pour plus d’informations, consultez [Mettre en correspondance une occurrence ou plus](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-).|+|`e.+d` correspond à « eed » dans « feeder », mais pas à « ed ».|
|Correspond à n'importe quel caractère une ou plusieurs fois (caractère générique ?)|.+|`e.+e` correspond à "eede" dans "feeder", mais pas à "ee".|
|Correspond à zéro ou plusieurs occurrences de l'expression précédente (correspond au minimum de caractères possible). Pour plus d’informations, consultez [Mettre en correspondance zéro occurrence ou plus (correspondance paresseuse)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-lazy-match-).|*?|`e.*?e` correspond à "ee" dans "feeder", mais pas à "eede".|
|Correspond à une ou plusieurs occurrences de l'expression précédente (correspond au minimum de caractères possible). Pour plus d’informations, consultez [Mettre en correspondance une occurrence ou plus (correspondance paresseuse)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-lazy-match-).|+?|`e.+?e` correspond à "ente" et "erprise" dans "enterprise", mais pas au mot entier "enterprise".|
|Ancre la chaîne de correspondance [au début d'une ligne ou d'une chaîne](/dotnet/standard/base-types/anchors-in-regular-expressions#start-of-string-or-line-)|^|`^car` correspond au mot "car" uniquement quand il apparaît au début d’une ligne.|
|Ancre la chaîne de correspondance à la [fin d'une ligne](/dotnet/standard/base-types/anchors-in-regular-expressions#end-of-string-or-line-)|\r?$|`end\r?$` correspond au mot "end" uniquement quand il apparaît à la fin d’une ligne.|
|Ancre la chaîne de correspondance à la fin du fichier|$|`end$` correspond au mot "end" uniquement quand il apparaît à la fin du fichier.|
|Correspond à n'importe quel caractère unique d'un ensemble|[abc]|`b[abc]` correspond à "ba", "bb" et "bc".|
|Correspond à n'importe quel caractère dans une plage de caractères|[a-f]|`be[n-t]` correspond à "bet" dans "between", à "ben" dans "beneath" et à "bes" dans "beside", mais pas à "below".|
|Capture et numérote implicitement l'expression contenue dans les parenthèses|()|`([a-z])X\1` correspond à "aXa" et à "bXb", mais pas à "aXb". « \1 » fait référence au premier groupe d’expressions « [a-z] ». Pour plus d’informations, consultez [Groupes de capture et modèles de remplacement](#capture-groups-and-replacement-patterns). |
|Invalide une correspondance|(?!abc)|`real(?!ity)` correspond à "real" dans "realty" et dans "really", mais pas dans "reality". Trouve également le deuxième « real » (mais pas le premier « real ») dans « realityreal ».|
|Correspond à n'importe quel caractère qui ne figure pas dans un ensemble donné de caractères. Pour plus d’informations, consultez [Groupe de caractères négatif](/dotnet/standard/base-types/character-classes-in-regular-expressions#negative-character-group-).|[^abc]|`be[^n-t]` correspond à "bef" dans "before », à "beh" dans "behind" et à "bel" dans "below", mais pas à "beneath".|
|Correspond à l'expression placée avant ou après le symbole|&#124;|`(sponge\|mud) bath` correspond à "sponge bath" et à "mud bath".|
|[Crée une séquence d'échappement](/dotnet/standard/base-types/character-escapes-in-regular-expressions) pour le caractère placé après la barre oblique inverse| \\ |`\^` correspond au caractère ^.|
|Spécifie le nombre d'occurrences du caractère ou du groupe précédent. Pour plus d’informations, consultez [Mettre en correspondance exactement n occurrences](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-exactly-n-times-n).|{n}, où n est le nombre d'occurrences|`x(ab){2}x` correspond à "xababx", et `x(ab){2,3}x` correspond à "xababx" et à "xabababx", mais pas à "xababababx".|
|[Mettre en correspondance un texte dans une catégorie Unicode](/dotnet/standard/base-types/character-classes-in-regular-expressions#unicode-category-or-unicode-block-p). Pour plus d’informations sur les classes de caractères Unicode, consultez [Propriétés des caractères de la norme Unicode 5.2](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf).|\p{X}, où "X" est le numéro Unicode.|`\p{Lu}` correspond à "T" et à "D" dans "Thomas Doe".|
|[Correspond à la limite d'un mot](/dotnet/standard/base-types/anchors-in-regular-expressions#word-boundary-b)|\b (en dehors d’une classe de caractères `\b` spécifie une limite de mot et, à l’intérieur d’une classe de caractères, `\b` spécifie un retour arrière)|`\bin` correspond à "in" dans "inside", mais pas dans "pinto".|
|Correspond à un saut de ligne (c’est-à-dire un retour chariot suivi d’une nouvelle ligne)|\r?\n|`End\r?\nBegin` correspond à "End" et à "Begin" uniquement quand "END" est la dernière chaîne d’une ligne et "Begin" la première chaîne de la ligne suivante.|
|Mettre en correspondance avec n’importe quel [caractère alphabétique](/dotnet/standard/base-types/character-classes-in-regular-expressions#word-character-w)|\w|`a\wd` correspond à "add" et à "a1d", mais pas à "a d".|
|Correspond à n'importe quel [espace blanc](/dotnet/standard/base-types/character-classes-in-regular-expressions#whitespace-character-s)|\s|`Public\sInterface` correspond à l’expression "Public Interface".|
|Mettre en correspondance avec n’importe quel [caractère numérique décimal](/dotnet/standard/base-types/character-classes-in-regular-expressions#decimal-digit-character-d)|\d|`\d` correspond à "3" dans "3456", à "2" dans "23" et à "1" dans "1".|
|Correspond à un caractère Unicode|\uXXXX où XXXX spécifie la valeur du caractère Unicode.|`\u0065` correspond au caractère "e".|
|Correspond à un identificateur|\b[\_\w-[0-9]][\_\w]*\b|Correspond à « type1 » mais pas à « &type1 » ni « #define ».|
|Correspond à une chaîne entre guillemets|((\\".+?\\")&#124;('.+?'))|Correspond à n'importe quelle chaîne entre apostrophes ou guillemets.|
|Correspond à un nombre hexadécimal|\b0[xX]([0-9a-fA-F]+\)\b|Correspond à « 0xc67f » mais pas à « 0xc67g ».|
|Correspond à des nombres entiers et décimaux|\b[0-9]*\\.\*[0-9]+\b|Correspond à « 1,333 ».|

> [!TIP]
> Dans les systèmes d’exploitation Windows, la plupart des lignes se terminent par « \r\n » (retour chariot suivi d’une nouvelle ligne). Ces caractères ne sont pas visibles, mais ils sont présents dans l’éditeur et sont passés au service d’expressions régulières de .NET.

## <a name="capture-groups-and-replacement-patterns"></a>Groupes de capture et modèles de remplacement

Un groupe de capture délimite une sous-expression d’une expression régulière et capture une sous-chaîne d’une chaîne d’entrée. Vous pouvez utiliser les groupes de capture dans l’expression régulière elle-même (par exemple pour rechercher un mot en double), ou dans un modèle de remplacement. Pour plus d’informations, consultez [Constructions de regroupement dans les expressions régulières](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions).

Pour créer un groupe de capture numéroté, placez la sous-expression entre parenthèses dans le modèle d’expression régulière. Les captures sont numérotées automatiquement de la gauche vers la droite en fonction de l'ordre des parenthèses ouvrantes dans l'expression régulière. Pour accéder au groupe capturé :

- **dans l’expression régulière** : Utilisez `\number`. Par exemple, `\1` dans l’expression régulière `(\w+)\s\1` fait référence au premier groupe de capture `(\w+)`.

- **dans un modèle de remplacement** : Utilisez `$number`. Par exemple, l’expression régulière groupée `(\d)([a-z])` définit deux groupes : le premier contient un chiffre décimal unique tandis que le deuxième contient un caractère unique compris entre **a** et **z**. L’expression recherche quatre correspondances dans la chaîne suivante : **1a 2b 3c 4d**. La chaîne de remplacement `z$1` référence le premier groupe uniquement (`$1`) et convertit la chaîne en **z1 z2 z3 z4**.

L’illustration suivante montre une expression régulière `(\w+)\s\1` et une chaîne de remplacement `$1`. L’expression régulière et le modèle de remplacement font référence au premier groupe de capture qui a reçoit automatiquement le numéro 1. Lorsque vous choisissez **Remplacer tout** dans la boîte de dialogue **Remplacement rapide** de Visual Studio, les mots répétés sont supprimés du texte.

![Remplacement rapide montrant un groupe de capture numéroté dans Visual Studio](media/numbered-capture-group.png)

> [!TIP]
> Assurez-vous que le bouton **Utiliser des expressions régulières** est sélectionné dans la boîte de dialogue **Remplacement rapide**.

### <a name="named-capture-groups"></a>Groupes de capture nommés

Au lieu d’utiliser la numérotation automatique d’un groupe de capture, vous pouvez lui donner un nom. La syntaxe pour un groupe de capture nommé est `(?<name>subexpression)`.

Les groupes de capture nommés, tout comme les groupes numérotés, peuvent être utilisés dans l’expression régulière elle-même ou dans un modèle de remplacement. Pour accéder au groupe de capture nommé :

- **dans l’expression régulière** : Utilisez `\k<name>`. Par exemple, `\k<repeated>` dans l’expression régulière `(?<repeated>\w+)\s\k<repeated>` fait référence au groupe de capture nommé `repeated` et dont la sous-expression est `\w+`.

- **dans un modèle de remplacement** : Utilisez `${name}`. Par exemple, `${repeated}`.

Par exemple, l’illustration suivante montre une expression régulière `(?<repeated>\w+)\s\k<repeated>` et une chaîne de remplacement `${repeated}`. L’expression régulière et le modèle de remplacement font référence au groupe de capture nommé `repeated`. Lorsque vous choisissez **Remplacer tout** dans la boîte de dialogue **Remplacement rapide** de Visual Studio, les mots répétés sont supprimés du texte.

![Remplacement rapide montrant un groupe de capture nommé dans Visual Studio](media/named-capture-group.png)

> [!TIP]
> Assurez-vous que le bouton **Utiliser des expressions régulières** est sélectionné dans la boîte de dialogue **Remplacement rapide**.

Pour plus d'informations sur les groupes de capture nommés, voir [Sous-expressions mises en correspondance nommées](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions#named-matched-subexpressions). Pour plus d’informations sur les expressions régulières utilisées dans les modèles de remplacement, consultez [Substitutions dans les expressions régulières](/dotnet/standard/base-types/substitutions-in-regular-expressions).

## <a name="see-also"></a>Voir aussi

- [Langage des expressions régulières](/dotnet/standard/base-types/regular-expression-language-quick-reference)
- [Rechercher et remplacer du texte](../ide/finding-and-replacing-text.md)
