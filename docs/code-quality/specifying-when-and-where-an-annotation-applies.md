---
title: Spécifiant le moment où une Annotation est applicable et | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4413f547429e88346c4d977cff4d5b93995a1741
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Spécification du moment où une annotation est applicable et dans quel cas
Lorsqu’une annotation est conditionnelle, elle peut nécessiter des autres annotations pour spécifier que l’analyseur.  Par exemple, si une fonction a une variable qui peut être synchrone ou asynchrone, la fonction se comporte comme suit : dans le cas synchrone il finit par réussit toujours, mais dans le cas asynchrone, il signale une erreur si elle ne peut pas réussir immédiatement. Lorsque la fonction est appelée de manière synchrone, la vérification de la valeur de résultat ne fournit aucune valeur à l’Analyseur de code, car il n'aurait pas retourné.  Toutefois, lorsque la fonction est appelée de façon asynchrone et le résultat de fonction n’est pas activé, une erreur grave peut se produire. Cet exemple illustre une situation dans laquelle vous pouvez utiliser la `_When_` annotation, décrite plus loin dans cet article : pour activer la recherche.  
  
## <a name="structural-annotations"></a>Annotations de la structure  
 Pour contrôler quand et où les annotations s’appliquent, utilisez les annotations de la structure suivantes.  
  
|Annotation|Description|  
|----------------|-----------------|  
|`_At_(expr, anno-list)`|`expr` est une expression qui produit une lvalue. Les annotations dans `anno-list` sont appliquées à l’objet nommé par `expr`. Pour chaque annotation dans `anno-list`, `expr` est interprétée en condition préalable, si l’annotation est interprétée de condition préalable, post-condition if l’annotation est interprétée dans la condition préalable.|  
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` est une expression qui produit une lvalue. Les annotations dans `anno-list` sont appliquées à l’objet nommé par `expr`. Pour chaque annotation dans `anno-list`, `expr` est interprétée en condition préalable, si l’annotation est interprétée de condition préalable, post-condition if l’annotation est interprétée dans la condition préalable.<br /><br /> `iter` est le nom d’une variable de portée est limitée à l’annotation (comprend `anno-list`). `iter` a un type implicite `long`. Les variables portant le même nommés dans toute portée englobante sont masqués à partir de l’évaluation.<br /><br /> `elem-count` est une expression qui correspond à un entier.|  
|`_Group_(anno-list)`|Les annotations dans `anno-list` sont tous considérés comme ayant un qualificateur qui s’applique à l’annotation de groupe est appliquée à chaque annotation.|  
|`_When_(expr, anno-list)`|`expr` est une expression qui peut être convertie en `bool`. Lorsqu’elle est différente de zéro (`true`), les annotations sont spécifiées dans `anno-list` sont considérés comme applicable.<br /><br /> Par défaut, pour chaque annotation dans `anno-list`, `expr` est interprété comme à l’aide de valeurs d’entrée si l’annotation est une condition préalable, et en utilisant les valeurs de sortie si l’annotation est une condition préalable. Pour remplacer la valeur par défaut, vous pouvez utiliser la `_Old_` intrinsèque lors de l’évaluation d’une condition préalable pour indiquer que les valeurs d’entrée doivent être utilisés. **Remarque :** des annotations peuvent être activées suite à l’aide de `_When_` si une valeur mutable : par exemple, `*pLength`— est requise car le résultat de `expr` dans la condition préalable peut différer de son évaluée résultat dans la condition préalable.|  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’Annotations SAL pour réduire les défauts du Code C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Présentation de SAL](../code-quality/understanding-sal.md)   
 [Annotation de paramètres de fonction et valeurs de retour](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotation du comportement de la fonction](../code-quality/annotating-function-behavior.md)   
 [Les structures et Classes d’annotation](../code-quality/annotating-structs-and-classes.md)   
 [Annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md)   
 [Fonctions intrinsèques](../code-quality/intrinsic-functions.md)   
 [Meilleures pratiques et exemples](../code-quality/best-practices-and-examples-sal.md)