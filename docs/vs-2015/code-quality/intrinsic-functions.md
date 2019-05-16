---
title: Fonctions intrinsèques | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: e5284ae41f961d8e027590b4296037236e7108f6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65699436"
---
# <a name="intrinsic-functions"></a>Fonctions intrinsèques
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Une expression dans SAL peut être une expression C/C++ condition qu’il soit une expression qui n’a pas d’effets secondaires, par exemple, ++,--et les appels de fonction tous avoir des effets secondaires dans ce contexte.  Toutefois, SAL fournit certains objets de type fonction et certains symboles réservés qui peuvent être utilisées dans les expressions de SAL. Ils sont désignés comme *fonctions intrinsèques*.  
  
## <a name="general-purpose"></a>Usage général  
 Les annotations de fonction intrinsèques suivantes fournissent des utilitaires générales pour SAL.  
  
|Annotation|Description|  
|----------------|-----------------|  
|`_Curr_`|Synonyme de l’objet qui est actuellement en cours d’annotation.  Lorsque le `_At_` annotation est en cours d’utilisation, `_Curr_` est le même que le premier paramètre de `_At_`.  Sinon, il est le paramètre ou la valeur de retour de fonction entière/auquel l’annotation est lexicalement associée.|  
|`_Inexpressible_(expr)`|Exprime une situation où la taille d’une mémoire tampon est trop complexe pour représenter à l’aide d’une expression d’annotation, par exemple, quand elle est calculée en analysant un jeu de données d’entrée et de puis comptage des membres sélectionnés.|  
|`_Nullterm_length_(param)`|`param` est le nombre d’éléments dans la mémoire tampon jusqu'à mais ne pas y compris une marque de fin null. Il peut être appliqué à une mémoire tampon de type non agrégé, non void.|  
|`_Old_(expr)`|Lorsqu’elle est évaluée de la précondition, `_Old_` retourne la valeur d’entrée `expr`.  Lorsqu’elle est évaluée dans la condition préalable, il retourne la valeur `expr` telle qu’elle est évaluée dans la condition préalable.|  
|`_Param_(n)`|Le `n`ième paramètre à une fonction, en partant de 1 à `n`, et `n` est une constante intégrale littéral. Si le paramètre est nommé, cette annotation est identique à accéder à la paramètre par nom. **Remarque :** `n` peuvent faire référence aux paramètres positionnels sont définies par les points de suspension, ou peuvent être utilisés dans les prototypes de fonction où les noms ne sont pas utilisés.|  
|`return`|Le C/C++ de mot clé réservé `return` peut être utilisé pour indiquer la valeur de retour d’une fonction dans une expression de SAL.  La valeur est disponible uniquement dans l’état de la publication ; Il est une erreur de syntaxe à utiliser dans un état antérieur.|  
  
## <a name="string-specific"></a>Chaîne spécifique  
 Les annotations suivantes de la fonction intrinsèque permettent une manipulation de chaînes. Les quatre de ces fonctions ont la même fonction : pour retourner le nombre d’éléments de type qui se trouve avant une marque de fin null. Les différences sont les types de données dans les éléments qui portent le nom. Notez que si vous souhaitez spécifier la longueur d’un par un caractère null de la mémoire tampon qui n’est pas composée de caractères, utilisez la `_Nullterm_length_(param)` annotation à partir de la section précédente.  
  
|Annotation|Description|  
|----------------|-----------------|  
|`_String_length_(param)`|`param` est le nombre d’éléments dans la chaîne jusqu'à mais ne pas y compris une marque de fin null. Cette annotation est réservée pour les types de chaîne de caractères.|  
|`strlen(param)`|`param` est le nombre d’éléments dans la chaîne jusqu'à mais ne pas y compris une marque de fin null. Cette annotation est réservée pour utilisation sur le caractère tableaux et ressemble à la fonction Runtime C [strlen()](https://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2).|  
|`wcslen(param)`|`param` est le nombre d’éléments dans la chaîne jusqu'à (mais sans inclure) un terminateur null. Cette annotation est réservée pour utilisation sur le caractère large tableaux et ressemble à la fonction Runtime C [wcslen()](https://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2).|  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’Annotations SAL pour réduire les défauts du Code C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Présentation de SAL](../code-quality/understanding-sal.md)   
 [Annotation des paramètres de fonction et valeurs de retour](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotation du comportement de la fonction](../code-quality/annotating-function-behavior.md)   
 [Annoter les Classes et Structs](../code-quality/annotating-structs-and-classes.md)   
 [Annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md)   
 [Spécifiant le moment où une Annotation est applicable et](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Bonnes pratiques et exemples](../code-quality/best-practices-and-examples-sal.md)
