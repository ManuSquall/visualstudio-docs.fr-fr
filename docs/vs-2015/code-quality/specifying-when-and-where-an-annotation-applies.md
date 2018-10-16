---
title: Spécifiant le moment où une Annotation est applicable et | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
caps.latest.revision: 9
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c4772dc980743db131002dbde80346836e9dc4c0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49303353"
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Spécification du moment où une annotation est applicable et dans quel cas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsqu’une annotation est conditionnelle, elle peut nécessiter des autres annotations pour spécifier que, à l’analyseur.  Par exemple, si une fonction comporte une variable qui peut être synchrone ou asynchrone, la fonction se comporte comme suit : dans le cas synchrone il finit par réussit toujours, mais dans le cas asynchrone, il signale une erreur si elle ne peut pas réussir immédiatement. Lorsque la fonction est appelée de manière synchrone, en vérifiant la valeur de résultat ne fournit aucune valeur pour l’Analyseur de code, car il n'aurait pas retourné.  Toutefois, lorsque la fonction est appelée de façon asynchrone et le résultat de la fonction n’est pas activé, une erreur grave peut se produire. Cet exemple illustre une situation dans laquelle vous pouvez utiliser le `_When_` annotation, décrite plus loin dans cet article, pour activer la vérification.  
  
## <a name="structural-annotations"></a>Annotations structurelles  
 Pour contrôler quand et où appliquent des annotations, utilisez les annotations structurelles suivantes.  
  
|Annotation|Description|  
|----------------|-----------------|  
|`_At_(expr, anno-list)`|`expr` est une expression qui produit une lvalue. Les annotations dans `anno-list` sont appliquées à l’objet nommé par `expr`. Pour chaque annotation dans `anno-list`, `expr` est interprété dans la condition préalable si l’annotation est interprétée dans les conditions préalables et in post-condition si l’annotation est dans la condition préalable.|  
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` est une expression qui produit une lvalue. Les annotations dans `anno-list` sont appliquées à l’objet nommé par `expr`. Pour chaque annotation dans `anno-list`, `expr` est interprété dans la condition préalable si l’annotation est interprétée dans la condition préalable et in post-condition si l’annotation est dans la condition préalable.<br /><br /> `iter` est le nom d’une variable de portée est limitée à l’annotation (comprend `anno-list`). `iter` a un type implicit `long`. Variables portant le même nommés dans n’importe quelle portée englobante sont masqués à partir de la version d’évaluation.<br /><br /> `elem-count` est une expression qui correspond à un entier.|  
|`_Group_(anno-list)`|Les annotations dans `anno-list` sont tous considérés comme ayant un qualificateur qui s’applique à l’annotation de groupe est appliquée à chaque annotation.|  
|`_When_(expr, anno-list)`|`expr` est une expression qui peut être convertie en `bool`. Quand il est différent de zéro (`true`), les annotations sont spécifiées dans `anno-list` sont considérés comme applicable.<br /><br /> Par défaut, pour chaque annotation dans `anno-list`, `expr` est interprétée comme en utilisant les valeurs d’entrée si l’annotation est une condition préalable, et en tant qu’en utilisant les valeurs de sortie si l’annotation est une condition préalable. Pour remplacer la valeur par défaut, vous pouvez utiliser le `_Old_` intrinsèque lorsque vous évaluez une condition préalable pour indiquer que les valeurs d’entrée doivent être utilisés. **Remarque :** des annotations peuvent être activées par conséquent à l’aide de `_When_` si une valeur mutable — par exemple, `*pLength`— est impliqué, car le résultat évalué de `expr` dans la condition préalable peut différer son évaluée résultat dans la condition préalable.|  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’Annotations SAL pour réduire les défauts du Code C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Présentation de SAL](../code-quality/understanding-sal.md)   
 [Annotation des paramètres de fonction et valeurs de retour](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotation du comportement de la fonction](../code-quality/annotating-function-behavior.md)   
 [Annoter les Classes et Structs](../code-quality/annotating-structs-and-classes.md)   
 [Annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md)   
 [Fonctions intrinsèques](../code-quality/intrinsic-functions.md)   
 [Bonnes pratiques et exemples](../code-quality/best-practices-and-examples-sal.md)



