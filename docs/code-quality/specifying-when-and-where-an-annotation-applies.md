---
title: "Sp&#233;cification du moment o&#249; une annotation est applicable et dans quel cas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_Group_"
  - "_At_"
  - "_When_"
  - "_At_buffer_"
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Sp&#233;cification du moment o&#249; une annotation est applicable et dans quel cas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsqu'une annotation est conditionnelle, elle peut nécessiter d'autres annotations pour le spécifier à l'analyseur.  Par exemple, si une fonction possède une variable qui peut être synchrone ou asynchrone, la fonction se comporte comme suit : Dans le cas synchrone, elle fonctionne toujours, mais dans le cas asynchrone, elle renvoie une erreur si elle ne réussit pas immédiatement.  Lorsque la fonction est appelée de façon synchrone, vérifier le fait que la valeur de résultat est contrôlée ne fournit aucune valeur à l'analyseur de code car il ne se serait pas retourné.  Toutefois, lorsque la fonction est appelée de façon asynchrone et le résultat de fonction n'est pas activée, une erreur grave s'est peut\-être produite.  Cet exemple montre une situation dans laquelle vous pouvez utiliser l'annotation `_When_` décrit plus loin dans cette article pour activer l'activation.  
  
## Annotations structurelles  
 Pour contrôler quand et où les annotations s'appliquent, utilisez les annotations structurelles suivantes.  
  
|Annotation|Description|  
|----------------|-----------------|  
|`_At_(expr, anno-list)`|`expr` est une expression qui retourne une lvalue.  Les annotations dans `anno-list` sont appliquées à l'objet nommé par `expr`.  Pour chaque annotation en `anno-list`, `expr` est interprété dans la condition préalable si l'annotation est interprétée dans la condition préalable, et après la condition si l'annotation est interprétée après dans la condition.|  
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` est une expression qui retourne une lvalue.  Les annotations dans `anno-list` sont appliquées à l'objet nommé par `expr`.  Pour chaque annotation en `anno-list`, `expr` est interprétée dans la condition préalable si l'annotation est interprétée dans la condition préalable, et après la condition si l'annotation est interprétée après dans la condition.<br /><br /> `iter` est le nom d'une variable qui est limitée à l'annotation \(y compris `anno-list`\).  `iter` a un type implicite `long`.  Les variables de manière identique nommées dans une portée englobante sont masquées de l'évaluation.<br /><br /> `elem-count` est une expression qui correspond à un entier.|  
|`_Group_(anno-list)`|Toutes les annotations dans `anno-list` sont considérées comme ayant un qualificateur qui s'applique à l'annotation de groupe appliquée à chaque annotation.|  
|`_When_(expr, anno-list)`|`expr` est une expression qui peut être convertie en `bool`.  Lorsqu'elle est non nulle \(`true`\) les annotations qui sont spécifiées dans `anno-list` sont considérées comme applicables.<br /><br /> Par défaut, pour chaque annotation en `anno-list`, `expr` est interprétée à l'aide des valeurs d'entrée si l'annotation est une condition préalable, et des valeurs de sortie si l'annotation est une condition postérieure.  Pour substituer la valeur par défaut, vous pouvez utiliser l'intrinsèque d' `_Old_` lorsque vous évaluez une condition pour indiquer que les valeurs d'entrée doivent être utilisées. **Note:**  Les annotations peuvent être activées en conséquence de l'utilisation de `_When_` si une valeur mutable \(par exemple, `*pLength`\) est sous\-entendue parce que le résultat de l'évaluation de `expr` dans la condition préalable peut être différent de celui obtenu en après condition.|  
  
## Voir aussi  
 [Utilisation d’annotations SAL pour réduire les défauts du code C\/C\+\+](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Présentation de SAL](../code-quality/understanding-sal.md)   
 [Annotation de paramètres de fonction et valeurs de retour](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotation du comportement d’une fonction](../code-quality/annotating-function-behavior.md)   
 [Structs et classes d’annotation](../code-quality/annotating-structs-and-classes.md)   
 [Annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md)   
 [Fonctions intrinsèques](../code-quality/intrinsic-functions.md)   
 [Meilleures pratiques et exemples](../code-quality/best-practices-and-examples-sal.md)