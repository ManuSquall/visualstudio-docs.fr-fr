---
title: Fonctions intrinsèques
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 65a5272d74e1987cd7838932182e7e59c9c53f21
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923944"
---
# <a name="intrinsic-functions"></a>Fonctions intrinsèques
Une expression dans SAL peut être une expression CC++ /, à condition qu’il s’agisse d’une expression qui n’a pas d’effets secondaires, par exemple + +,--, et les appels de fonction ont tous des effets secondaires dans ce contexte.  Toutefois, SAL fournit des objets de type fonction et certains symboles réservés qui peuvent être utilisés dans les expressions SAL. Ils sont appelés *fonctions intrinsèques*.

## <a name="general-purpose"></a>Usage général
Les annotations de fonction intrinsèques suivantes fournissent un utilitaire général pour SAL.

|Annotation|Description|
|----------------|-----------------|
|`_Curr_`|Synonyme de l’objet qui est actuellement annoté.  Lorsque l' `_At_` annotation est utilisée, `_Curr_` est le même que le premier paramètre de `_At_`.  Dans le cas contraire, il s’agit du paramètre ou de la totalité de la fonction ou de la valeur de retour avec laquelle l’annotation est associée de manière lexicale.|
|`_Inexpressible_(expr)`|Exprime une situation où la taille d’une mémoire tampon est trop complexe pour être représentée à l’aide d’une expression d’annotation, par exemple lorsqu’elle est calculée en analysant un jeu de données d’entrée, puis en comptant les membres sélectionnés.|
|`_Nullterm_length_(param)`|`param`nombre d’éléments dans la mémoire tampon jusqu’à un terminateur null, sans y inclure. Elle peut être appliquée à n’importe quelle mémoire tampon de type non-agrégat et non void.|
|`_Old_(expr)`|Lorsqu’elle est évaluée dans la `_Old_` condition préalable, retourne `expr`la valeur d’entrée.  Lorsqu’elle est évaluée dans un État postérieur, elle retourne la `expr` valeur telle qu’elle aurait été évaluée dans la condition préalable.|
|`_Param_(n)`|Le `n`th paramètre d’une fonction, en comptant de `n`1 à `n` , et est une constante intégrale littérale. Si le paramètre est nommé, cette annotation est identique à l’accès au paramètre par son nom. **Remarque:** `n` peut faire référence aux paramètres positionnels définis par des points de suspension ou peut être utilisé dans les prototypes de fonction où les noms ne sont pas utilisés.|
|`return`|Le mot cléC++ `return` C/reserved peut être utilisé dans une expression SAL pour indiquer la valeur de retour d’une fonction.  La valeur est uniquement disponible dans l’état de publication; Il s’agit d’une erreur de syntaxe pour l’utiliser dans un état antérieur.|

## <a name="string-specific"></a>Spécifique à la chaîne
Les annotations de fonctions intrinsèques suivantes permettent la manipulation de chaînes. Les quatre fonctions ont le même objectif: pour retourner le nombre d’éléments du type qui est trouvé avant un terminateur null. Les différences sont les genres de données dans les éléments auxquels il est question. Notez que, si vous souhaitez spécifier la longueur d’une mémoire tampon se terminant par un caractère null qui ne se compose pas `_Nullterm_length_(param)` de caractères, utilisez l’annotation de la section précédente.

|Annotation|Description|
|----------------|-----------------|
|`_String_length_(param)`|`param`nombre d’éléments de la chaîne jusqu’à un terminateur null, sans y inclure. Cette annotation est réservée pour les types chaîne de caractères.|
|`strlen(param)`|`param`nombre d’éléments de la chaîne jusqu’à un terminateur null, sans y inclure. Cette annotation est réservée à une utilisation sur des tableaux de caractères et ressemble à la fonction Runtime C [strlen ()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|
|`wcslen(param)`|`param`nombre d’éléments dans la chaîne jusqu’à une marque de fin null (sans l’inclure). Cette annotation est réservée à une utilisation sur des tableaux de caractères larges et ressemble à la fonction Runtime C [wcslen ()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|

## <a name="see-also"></a>Voir aussi

- [Utilisation d’annotations SAL pour réduire les défauts du code C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Présentation de SAL](../code-quality/understanding-sal.md)
- [Annotation des paramètres de fonction et des valeurs de retour](../code-quality/annotating-function-parameters-and-return-values.md)
- [Annotation du comportement d’une fonction](../code-quality/annotating-function-behavior.md)
- [Annotations des structs et des classes](../code-quality/annotating-structs-and-classes.md)
- [Annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md)
- [Spécification du moment et de l’endroit où une annotation s’applique](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Bonnes pratiques et exemples](../code-quality/best-practices-and-examples-sal.md)