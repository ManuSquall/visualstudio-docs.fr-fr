---
title: Spécification du moment où une annotation est applicable et dans quel cas
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: f6efcc158ea0b5b2e44a5b9d0750bc897e442994
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271839"
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Spécification du moment où une annotation est applicable et dans quel cas
Lorsqu’une annotation est conditionnelle, elle peut nécessiter d’autres annotations pour la spécifier à l’analyseur.  Par exemple, si une fonction a une variable qui peut être synchrone ou asynchrone, la fonction se comporte comme suit : dans le cas synchrone, elle aboutit toujours, mais dans le cas asynchrone, elle signale une erreur si elle ne peut pas aboutir immédiatement. Lorsque la fonction est appelée de manière synchrone, la vérification de la valeur de résultat n’apporte aucune valeur à l’analyseur de code car il n’aurait pas été retourné.  Toutefois, lorsque la fonction est appelée de manière asynchrone et que le résultat de la fonction n’est pas vérifié, une erreur grave peut se produire. Cet exemple illustre une situation dans laquelle vous pouvez utiliser l’annotation `_When_`, décrite plus loin dans cet article, pour activer la vérification.

## <a name="structural-annotations"></a>Annotations structurelles
Pour contrôler quand et où les annotations s’appliquent, utilisez les annotations structurelles suivantes.

|Annotation|Description|
|----------------|-----------------|
|`_At_(expr, anno-list)`|`expr` est une expression qui produit une lvalue. Les annotations de `anno-list` sont appliquées à l’objet qui est nommé par `expr`. Pour chaque annotation dans `anno-list`, `expr` est interprétée dans la condition préalable si l’annotation est interprétée dans la condition préalable, et dans le cas où l’annotation est interprétée dans une condition de publication.|
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` est une expression qui produit une lvalue. Les annotations de `anno-list` sont appliquées à l’objet qui est nommé par `expr`. Pour chaque annotation dans `anno-list`, `expr` est interprétée dans la condition préalable si l’annotation est interprétée comme condition préalable, et dans le cas où l’annotation est interprétée dans une condition postérieure.<br /><br /> `iter` est le nom d’une variable dont la portée correspond à celle de l’annotation (comprise entre `anno-list`). `iter` a un type implicite `long`. Les variables portant le même nom dans une portée englobante sont masquées de l’évaluation.<br /><br /> `elem-count` est une expression qui prend la valeur d’un entier.|
|`_Group_(anno-list)`|Les annotations dans `anno-list` sont toutes considérées comme ayant un qualificateur qui s’applique à l’annotation de groupe appliquée à chaque annotation.|
|`_When_(expr, anno-list)`|`expr` est une expression qui peut être convertie en `bool`. Lorsqu’il est différent de zéro (`true`), les annotations spécifiées dans `anno-list` sont considérées comme applicables.<br /><br /> Par défaut, pour chaque annotation dans `anno-list`, `expr` est interprété comme utilisant les valeurs d’entrée si l’annotation est une condition préalable et comme utilisant les valeurs de sortie si l’annotation est une condition postérieure. Pour remplacer la valeur par défaut, vous pouvez utiliser le `_Old_` intrinsèque lorsque vous évaluez une condition postérieure pour indiquer que les valeurs d’entrée doivent être utilisées. **Remarque :**  Différentes annotations peuvent être activées à la suite de l’utilisation de `_When_` si une valeur mutable (par exemple, `*pLength`) est impliquée, car le résultat évalué de `expr` dans la condition préalable peut différer de son résultat évalué dans une condition de publication.|

## <a name="see-also"></a>Voir aussi

- [Utilisation d’annotations SAL pour réduire les défauts du code C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Présentation de SAL](../code-quality/understanding-sal.md)
- [Annotation des paramètres de fonction et des valeurs de retour](../code-quality/annotating-function-parameters-and-return-values.md)
- [Annotation du comportement d’une fonction](../code-quality/annotating-function-behavior.md)
- [Annotations des structs et des classes](../code-quality/annotating-structs-and-classes.md)
- [Annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md)
- [Fonctions intrinsèques](../code-quality/intrinsic-functions.md)
- [Bonnes pratiques et exemples](../code-quality/best-practices-and-examples-sal.md)
