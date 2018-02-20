---
title: "Utilisation d’expressions régulières dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 077bb266e6ed55bfe59ec4e537b516ccde59e0c3
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="using-regular-expressions-in-visual-studio"></a>Utilisation d’expressions régulières dans Visual Studio

Visual Studio utilise les [expressions régulières du .NET Framework](/dotnet/standard/base-types/regular-expressions) pour rechercher et remplacer du texte.

## <a name="replacement-patterns"></a>Modèles de substitution

Pour plus d’informations sur les expressions régulières utilisées dans les modèles de remplacement, consultez [Substitutions dans les expressions régulières (Guide .NET)](/dotnet/standard/base-types/substitutions-in-regular-expressions). Pour utiliser un groupe de capture numéroté, la syntaxe est `$1` pour spécifier le groupe numéroté et `(x)` pour spécifier le groupe en question. Par exemple, l’expression régulière groupée `(\d)([a-z])` trouve quatre correspondances dans la chaîne suivante : **1a 2b 3c 4d**. La chaîne de remplacement `z$1` convertit cette chaîne en **z1 z2 z3 z4**.

## <a name="regular-expression-examples"></a>Exemples d’expressions régulières

Voici quelques exemples :

|Objectif|Expression|Exemple|
|-------------|----------------|-------------|
|Correspond à n'importe quel caractère unique (sauf un saut de ligne)|.|`a.o` correspond à "aro" dans "around" et à "abo" dans "about", mais pas à "acro" dans "across".|
|Correspond à zéro ou plusieurs occurrences de l'expression précédente (correspond à autant de caractères que possible)|*|`a*r` correspond à "r" dans "rack", à "rar" dans "ark" et à "aar" dans "aardvark"|
|Correspond à n'importe quel caractère zéro ou plusieurs fois (caractère générique *)|.*|c.*e correspond à « cke » dans « racket », à « comme » dans « commentaire » et à « code » dans « code »|
|Correspond à une ou plusieurs occurrences de l'expression précédente (correspond à autant de caractères que possible)|+|`e.+e` correspond à "eede" dans "feeder", mais pas à "ee".|
|Correspond à n'importe quel caractère une ou plusieurs fois (caractère générique ?)|.+|e.+e correspond à « eede » dans « feeder » mais pas à « ee ».|
|Correspond à zéro ou plusieurs occurrences de l'expression précédente (correspond au minimum de caractères possible)|*?|`e.*?e` correspond à "ee" dans "feeder", mais pas à "eede".|
|Correspond à une ou plusieurs occurrences de l'expression précédente (correspond au minimum de caractères possible)|+?|`e.+?e` correspond à "ente" et "erprise" dans "enterprise", mais pas au mot entier "enterprise".|
|Ancre la chaîne de correspondance au début d'une ligne ou d'une chaîne|^|`^car` correspond au mot "car" uniquement quand il apparaît au début d’une ligne.|
|Ancre la chaîne de correspondance à la fin d'une ligne|\r?$|`End\r?$` correspond au mot "end" uniquement quand il apparaît à la fin d’une ligne.|
|Correspond à n'importe quel caractère unique d'un ensemble|[abc]|`b[abc]` correspond à "ba", "bb" et "bc".|
|Correspond à n'importe quel caractère dans une plage de caractères|[a-f]|`be[n-t]` correspond à "bet" dans "between", à "ben" dans "beneath" et à "bes" dans "beside", mais pas à "below".|
|Capture et numérote implicitement l'expression contenue dans les parenthèses|()|`([a-z])X\1` correspond à "aXa" et à "bXb", mais pas à "aXb". ". « \1 » fait référence au premier groupe d’expressions « [a-z] ».|
|Invalide une correspondance|(?!abc)|`real (?!ity)` correspond à "real" dans "realty" et dans "really", mais pas dans "reality". Trouve également le deuxième « real » (mais pas le premier « real ») dans « realityreal ».|
|Correspond à n'importe quel caractère qui ne figure pas dans un ensemble donné de caractères|[^abc]|`be[^n-t]` correspond à "bef" dans "before », à "beh" dans "behind" et à "bel" dans "below", mais pas à "beneath".|
|Correspond à l'expression placée avant ou après le symbole.|&#124;|`(sponge&#124;mud) bath` correspond à "sponge bath" et à "mud bath".|
|Crée une séquence d'échappement pour le caractère placé après la barre oblique inverse|\\|`\^` correspond au caractère ^.|
|Spécifie le nombre d'occurrences du caractère ou du groupe précédent|{x}, où x est le nombre d'occurrences|`x(ab){2}x` correspond à "xababx", et `x(ab){2,3}x` correspond à "xababx" et à "xabababx", mais pas à "xababababx".|
|Met en correspondance du texte dans une classe de caractères Unicode, où « X » est le nombre Unicode. Pour plus d'informations sur les classes de caractères Unicode, consultez<br /><br /> [Propriétés des caractères de la norme Unicode 5.2](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf).|\p{X}|`\p{Lu}` correspond à "T" et à "D" dans "Thomas Doe".|
|Correspond à la limite d'un mot|`\b` (En dehors d’une classe de caractères, \b spécifie une limite de mot ; à l’intérieur d’une classe de caractères, \b spécifie un retour arrière.)|`\bin` correspond à "in" dans "inside", mais pas dans "pinto".|
|Correspond à un saut de ligne (c'est-à-dire un retour chariot suivi d'une nouvelle ligne)|\r?\n|`End\r?\nBegin` correspond à "End" et à "Begin" uniquement quand "END" est la dernière chaîne d’une ligne et "Begin" la première chaîne de la ligne suivante.|
|Correspond à n'importe quel caractère alphanumérique|\w|`a\wd` correspond à "add" et à "a1d", mais pas à "a d".|
|Correspond à n'importe quel espace blanc|(?([^\r\n])\s)|`Public\sInterface` correspond à l’expression "Public Interface".|
|Correspond à n'importe quel caractère numérique|\d|`\d` correspond à "3" dans "3456", à "2" dans "23" et à "1" dans "1".|
|Correspond à un caractère Unicode|\uXXXX où XXXX spécifie la valeur du caractère Unicode.|`\u0065` correspond au caractère "e".|
|Correspond à un identificateur|\b(_\w+&#124;[\w-[0-9\_]]\w*)\b|Correspond à « type1 » mais pas à « &type1 » ni « #define ».|
|Correspond à une chaîne entre guillemets|((\\".+?\\")&#124;('.+?'))|Correspond à n'importe quelle chaîne entre apostrophes ou guillemets.|
|Correspond à un nombre hexadécimal|\b0[xX]([0-9a-fA-F]\)\b|Correspond à « 0xc67f » mais pas à « 0xc67fc67f ».|
|Correspond à des nombres entiers et décimaux|\b[0-9]*\\.\*[0-9]+\b|Correspond à « 1,333 ».|

> [!TIP]
> Dans les systèmes d’exploitation Windows, la plupart des lignes se terminent par « \r\n » (retour chariot suivi d’une nouvelle ligne). Ces caractères ne sont pas visibles, mais sont présents dans l’éditeur et sont transmis au service d’expressions régulières .NET.

## <a name="see-also"></a>Voir aussi

[Recherche et remplacement de texte](../ide/finding-and-replacing-text.md)