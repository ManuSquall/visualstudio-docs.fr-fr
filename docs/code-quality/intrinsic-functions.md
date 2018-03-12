---
title: "Fonctions intrinsèques | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c25c76ba43c983a6029c8d50e183ccf839ef08bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="intrinsic-functions"></a>Fonctions intrinsèques
Une expression dans SAL peut être une expression C/C++ condition qu’il soit une expression qui n’a pas d’effets secondaires, par exemple, ++,--et les appels de fonction tous ont des effets secondaires dans ce contexte.  Toutefois, SAL fournit certains objets de type fonction et certains symboles réservés qui peuvent être utilisées dans les expressions de SAL. Ils sont désignés en tant que *des fonctions intrinsèques*.  
  
## <a name="general-purpose"></a>Usage général  
 Les annotations de fonction intrinsèques suivantes fournissent des utilitaires générales pour SAL.  
  
|Annotation|Description|  
|----------------|-----------------|  
|`_Curr_`|Un synonyme de l’objet qui est actuellement en cours d’annotation.  Lorsque le `_At_` annotation est en cours d’utilisation, `_Curr_` est le même que le premier paramètre de `_At_`.  Dans le cas contraire, il est le paramètre ou la valeur entière/retour de fonction à laquelle l’annotation est lexicalement associée.|  
|`_Inexpressible_(expr)`|Exprime une situation où la taille d’une mémoire tampon est trop complexe pour représenter à l’aide d’une expression d’annotation, par exemple, quand elle est calculée par l’analyse d’un jeu de données d’entrée et ensuite le comptage des membres sélectionnés.|  
|`_Nullterm_length_(param)`|`param`est le nombre d’éléments dans la mémoire tampon jusqu'à sans inclure un terminateur null. Il peut être appliqué à une mémoire tampon de type non agrégées, non void.|  
|`_Old_(expr)`|Lorsqu’elle est évaluée dans la condition préalable, `_Old_` retourne la valeur d’entrée `expr`.  Lorsqu’elle est évaluée dans la condition préalable, il retourne la valeur `expr` car il aurait été évalué dans une condition préalable.|  
|`_Param_(n)`|Le `n`ième paramètre à une fonction, en comptant à partir de 1 à `n`, et `n` est une constante intégrale littéral. Si le paramètre est nommé, cette annotation est identique à l’accès à la paramètre par nom. **Remarque :** `n` peuvent faire référence aux paramètres positionnels qui sont définies par les points de suspension, ou peuvent être utilisés dans les prototypes de fonction où les noms ne sont pas utilisés.|  
|`return`|Mot clé réservé de C/C++ `return` peut être utilisé pour indiquer la valeur de retour d’une fonction dans une expression de SAL.  La valeur est uniquement disponible dans l’état de la publication ; Il est une erreur de syntaxe à utiliser dans l’état des versions antérieures.|  
  
## <a name="string-specific"></a>Chaîne spécifique  
 Les annotations suivantes de la fonction intrinsèque permettent une manipulation de chaînes. Les quatre de ces fonctions ont la même fonction : pour retourner le nombre d’éléments du type qui se trouve avant une marque de fin null. Les différences sont les types de données dans les éléments qui portent le nom. Notez que si vous souhaitez spécifier la longueur d’une valeur null se terminant par la mémoire tampon qui n’est pas composé de caractères, utilisez la `_Nullterm_length_(param)` annotation à partir de la section précédente.  
  
|Annotation|Description|  
|----------------|-----------------|  
|`_String_length_(param)`|`param`est le nombre d’éléments dans la chaîne, mais ne pas y compris un terminateur null. Cette annotation est réservée pour les types de caractère de chaîne.|  
|`strlen(param)`|`param`est le nombre d’éléments dans la chaîne, mais ne pas y compris un terminateur null. Cette annotation est réservée pour l’utilisation de caractères les tableaux et ressemble à la fonction C Runtime [strlen()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|  
|`wcslen(param)`|`param`est le nombre d’éléments dans la chaîne de configuration (mais sans inclure) un terminateur null. Cette annotation est réservée pour utilisation sur un caractère large tableaux et ressemble à la fonction C Runtime [wcslen()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’Annotations SAL pour réduire les défauts du Code C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Présentation de SAL](../code-quality/understanding-sal.md)   
 [Annotation de paramètres de fonction et valeurs de retour](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotation du comportement de la fonction](../code-quality/annotating-function-behavior.md)   
 [Les structures et Classes d’annotation](../code-quality/annotating-structs-and-classes.md)   
 [Annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md)   
 [Spécification de quand et où une Annotation est applicable](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Meilleures pratiques et exemples](../code-quality/best-practices-and-examples-sal.md)