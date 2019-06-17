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
ms.openlocfilehash: 5fc2e1afa95c56dda79296a24f027fb93d62c585
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747740"
---
# <a name="use-regular-expressions-in-visual-studio"></a>Utiliser des expressions régulières dans Visual Studio

Visual Studio utilise des [expressions régulières de .NET](/dotnet/standard/base-types/regular-expressions) pour rechercher et remplacer du texte.

## <a name="replacement-patterns"></a>Modèles de substitution

Pour utiliser un groupe de capture numéroté, placez le groupe entre parenthèses dans le modèle d’expression régulière. Utilisez `$number`, où `number` est un entier commençant à 1, pour spécifier un groupe numéroté spécifique dans un modèle de remplacement. Par exemple, l’expression régulière groupée `(\d)([a-z])` définit deux groupes : le premier contient un chiffre décimal unique tandis que le deuxième contient un caractère unique compris entre **a** et **z**. L’expression recherche quatre correspondances dans la chaîne suivante : **1a 2b 3c 4d**. La chaîne de remplacement `z$1` référence le premier groupe uniquement et convertit la chaîne en **z1 z2 z3 z4**.

Pour plus d’informations sur les expressions régulières utilisées dans les modèles de remplacement, consultez [Substitutions dans les expressions régulières (Guide .NET)](/dotnet/standard/base-types/substitutions-in-regular-expressions).

## <a name="regular-expression-examples"></a>Exemples d’expressions régulières

Voici quelques exemples :

|Objectif|Expression|Exemple|
|-------------|----------------|-------------|
|Correspond à n'importe quel caractère unique (sauf un saut de ligne)|.|`a.o` correspond à "aro" dans "around" et à "abo" dans "about", mais pas à "acro" dans "across".|
|Correspond à zéro ou plusieurs occurrences de l'expression précédente (correspond à autant de caractères que possible)|*|`a*r` correspond à "r" dans "rack", à "rar" dans "ark" et à "aar" dans "aardvark"|
|Correspond à n'importe quel caractère zéro ou plusieurs fois (caractère générique *)|.*|`c.*e` correspond à « cke » dans « racket », à « comme » dans « commentaire » et à « code » dans « code ».|
|Correspond à une ou plusieurs occurrences de l'expression précédente (correspond à autant de caractères que possible)|+|`e.+d` correspond à « eed » dans « feeder », mais pas à « ed ».|
|Correspond à n'importe quel caractère une ou plusieurs fois (caractère générique ?)|.+|`e.+e` correspond à "eede" dans "feeder", mais pas à "ee".|
|Correspond à zéro ou plusieurs occurrences de l'expression précédente (correspond au minimum de caractères possible)|*?|`e.*?e` correspond à "ee" dans "feeder", mais pas à "eede".|
|Correspond à une ou plusieurs occurrences de l'expression précédente (correspond au minimum de caractères possible)|+?|`e.+?e` correspond à "ente" et "erprise" dans "enterprise", mais pas au mot entier "enterprise".|
|Ancre la chaîne de correspondance au début d'une ligne ou d'une chaîne|^|`^car` correspond au mot "car" uniquement quand il apparaît au début d’une ligne.|
|Ancre la chaîne de correspondance à la fin d'une ligne|\r?$|`end\r?$` correspond au mot "end" uniquement quand il apparaît à la fin d’une ligne.|
|Ancre la chaîne de correspondance à la fin du fichier|$|`end$` correspond au mot "end" uniquement quand il apparaît à la fin du fichier.|
|Correspond à n'importe quel caractère unique d'un ensemble|[abc]|`b[abc]` correspond à "ba", "bb" et "bc".|
|Correspond à n'importe quel caractère dans une plage de caractères|[a-f]|`be[n-t]` correspond à "bet" dans "between", à "ben" dans "beneath" et à "bes" dans "beside", mais pas à "below".|
|Capture et numérote implicitement l'expression contenue dans les parenthèses|()|`([a-z])X\1` correspond à "aXa" et à "bXb", mais pas à "aXb". « \1 » fait référence au premier groupe d’expressions « [a-z] ».|
|Invalide une correspondance|(?!abc)|`real(?!ity)` correspond à "real" dans "realty" et dans "really", mais pas dans "reality". Trouve également le deuxième « real » (mais pas le premier « real ») dans « realityreal ».|
|Correspond à n'importe quel caractère qui ne figure pas dans un ensemble donné de caractères|[^abc]|`be[^n-t]` correspond à "bef" dans "before », à "beh" dans "behind" et à "bel" dans "below", mais pas à "beneath".|
|Correspond à l'expression placée avant ou après le symbole.|&#124;|`(sponge\|mud) bath` correspond à "sponge bath" et à "mud bath".|
|Crée une séquence d'échappement pour le caractère placé après la barre oblique inverse| \\ |`\^` correspond au caractère ^.|
|Spécifie le nombre d'occurrences du caractère ou du groupe précédent|{x}, où x est le nombre d'occurrences|`x(ab){2}x` correspond à "xababx", et `x(ab){2,3}x` correspond à "xababx" et à "xabababx", mais pas à "xababababx".|
|Correspond à du texte dans une classe de caractères Unicode. Pour plus d'informations sur les classes de caractères Unicode, consultez<br /><br /> [Propriétés des caractères de la norme Unicode 5.2](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf).|\p{X}, où "X" est le numéro Unicode.|`\p{Lu}` correspond à "T" et à "D" dans "Thomas Doe".|
|Correspond à la limite d'un mot|\b (en dehors d’une classe de caractères `\b` spécifie une limite de mot et, à l’intérieur d’une classe de caractères, `\b` spécifie un retour arrière)|`\bin` correspond à "in" dans "inside", mais pas dans "pinto".|
|Correspond à un saut de ligne (c’est-à-dire un retour chariot suivi d’une nouvelle ligne).|\r?\n|`End\r?\nBegin` correspond à "End" et à "Begin" uniquement quand "END" est la dernière chaîne d’une ligne et "Begin" la première chaîne de la ligne suivante.|
|Correspond à n'importe quel caractère alphanumérique|\w|`a\wd` correspond à "add" et à "a1d", mais pas à "a d".|
|Correspond à n'importe quel espace blanc|\s|`Public\sInterface` correspond à l’expression "Public Interface".|
|Correspond à n'importe quel caractère numérique|\d|`\d` correspond à "3" dans "3456", à "2" dans "23" et à "1" dans "1".|
|Correspond à un caractère Unicode|\uXXXX où XXXX spécifie la valeur du caractère Unicode.|`\u0065` correspond au caractère "e".|
|Correspond à un identificateur|\b[\_\w-[0-9]][\_\w]*\b|Correspond à « type1 » mais pas à « &type1 » ni « #define ».|
|Correspond à une chaîne entre guillemets|((\\".+?\\")&#124;('.+?'))|Correspond à n'importe quelle chaîne entre apostrophes ou guillemets.|
|Correspond à un nombre hexadécimal|\b0[xX]([0-9a-fA-F]+\)\b|Correspond à « 0xc67f » mais pas à « 0xc67g ».|
|Correspond à des nombres entiers et décimaux|\b[0-9]*\\.\*[0-9]+\b|Correspond à « 1,333 ».|

> [!TIP]
> Dans les systèmes d’exploitation Windows, la plupart des lignes se terminent par « \r\n » (retour chariot suivi d’une nouvelle ligne). Ces caractères ne sont pas visibles, mais ils sont présents dans l’éditeur et sont passés au service d’expressions régulières de .NET.

## <a name="see-also"></a>Voir aussi

- [Rechercher et remplacer du texte](../ide/finding-and-replacing-text.md)
