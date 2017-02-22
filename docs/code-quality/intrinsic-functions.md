---
title: "Fonctions intrins&#232;ques | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_String_length_"
  - "_Param_"
  - "_Curr_"
  - "_Old_"
  - "_Nullterm_length_"
  - "_Inexpressible_"
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Fonctions intrins&#232;ques
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Une expression SAL peut être une expression C\/C\+\+ à condition que ce soit une expression qui n'a pas d'effet secondaire \- par exemple, \+\+, \-\-, et les appels de fonctions ont des effets secondaires dans ce contexte.  Toutefois, le SAL fournit des objets comme une fonction et des symboles réservés qui peuvent être utilisés dans les expressions SAL.  Celles\-ci sont appelés *fonctions intrinsèques*.  
  
## Utilisation universel  
 Les annotations instrinsic suivantes de fonction fournissent l'utilitaire général à utiliser SAL.  
  
|Annotation|Description|  
|----------------|-----------------|  
|`_Curr_`|Un synonyme pour l'objet actuellement annoté.  Lorsque l'annotation d' `_At_` est en cours de utilisation, `_Curr_` est le même que le premier paramètre de `_At_`.  Sinon, c'est le paramètre ou la fonction entière\/valeur de retour avec laquelle l'annotation est lexicale associée.|  
|`_Inexpressible_(expr)`|Exprime une situation où la taille d'une mémoire tampon est trop complexe pour représenter avec une expression d'annotation, par exemple lorsqu'elle est calculée en balayant un jeu de données d'entrée et en comptant les membres sélectionnés.|  
|`_Nullterm_length_(param)`|`param` est le nombre d'éléments dans la mémoire tampon jusqu'à la limite d'une marque de fin null.  Elle peut s'appliquer à toute mémoire tampon non agrégat, type non void.|  
|`_Old_(expr)`|Lorsqu'il est évalué dans la condition préalable, `_Old_` retourne la valeur d'entrée `expr`.  Une fois évaluée dans la condition après, elle retourne la valeur `expr` comme il aurait été évaluée dans la condition préalable.|  
|`_Param_(n)`|Le paramètre de Th d' `n`à une fonction, comptant entre 1 et `n`, et `n` est une constante intégrale littérale.  Si le paramètre est nommé, cette annotation identique à accéder au paramètre de nom. **Note:**  `n` peut faire référence aux paramètres positionnels définis par les points de suspension, ou peut être utilisé dans des prototypes de fonction où les noms ne sont pas utilisés.|  
|`return`|Le mot clé réservé `return` C\/C\+\+ peut être utilisé dans une expression SAL pour indiquer la valeur de retour d'une fonction.  La valeur est uniquement disponible dans l'état de publication; et c'est une erreur de syntaxe à utiliser dans un pré\-état.|  
  
## Détails de chaîne  
 Les annotations suivantes de fonction intrinsèque permettent de manipuler des chaînes.  Les quatre de ces fonctions atteint le même objectif : pour retourner le nombre d'éléments du type avez trouvé avant une marque de fin null.  Les différences sont des types de données des éléments qui sont mentionnés.  Notez que si vous souhaitez spécifier la longueur d'un tampon terminée par le caractère NULL qui n'est pas composée de caractères, utilisez l'annotation `_Nullterm_length_(param)` de la section précédente.  
  
|Annotation|Description|  
|----------------|-----------------|  
|`_String_length_(param)`|`param` est le nombre d'éléments dans la chaine jusqu'à la limite d'une marque de fin null.  Cette annotation est réservée pour les types de chaîne\-de\- caractère.|  
|`strlen(param)`|`param` est le nombre d'éléments dans la chaine jusqu'à la limite d'une marque de fin null.  Cette annotation est réservée pour une utilisation sur les tableaux de caractères, les mêmes que la fonction d'exécution [strlen\(\)](/visual-cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l)C.|  
|`wcslen(param)`|`param` est le nombre d'éléments dans la chaine jusqu'à la limite \(mais sans l'inclure\) d'une marque de fin null.  Cette annotation est réservée pour une utilisation sur les tableaux de caractères long, les mêmes que la fonction d'exécution [wcslen\(\)](/visual-cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l)C.|  
  
## Voir aussi  
 [Utilisation d’annotations SAL pour réduire les défauts du code C\/C\+\+](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Présentation de SAL](../code-quality/understanding-sal.md)   
 [Annotation de paramètres de fonction et valeurs de retour](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotation du comportement d’une fonction](../code-quality/annotating-function-behavior.md)   
 [Structs et classes d’annotation](../code-quality/annotating-structs-and-classes.md)   
 [Annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md)   
 [Spécification du moment où une annotation est applicable et dans quel cas](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Meilleures pratiques et exemples](../code-quality/best-practices-and-examples-sal.md)