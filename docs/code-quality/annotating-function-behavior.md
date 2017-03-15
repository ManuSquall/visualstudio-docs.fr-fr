---
title: "Annotation du comportement d’une fonction | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_On_failure_"
  - "_Return_type_success_"
  - "_Always_"
  - "_Maybe_raises_SEH_exception_"
  - "_Raises_SEH_exception_"
  - "_Called_from_function_class_"
  - "_Function_class_"
  - "_Must_inspect_result_"
  - "_Success_"
  - "_Check_return_"
  - "_Use_decl_annotations_"
ms.assetid: c0aa268d-6fa3-4ced-a8c6-f7652b152e61
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Annotation du comportement d’une fonction
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En plus d'annoter [les paramètres de fonction et les valeurs de retour](../code-quality/annotating-function-parameters-and-return-values.md), vous pouvez annoter les propriétés de la fonction entière.  
  
## Annotations de fonction  
 Les annotations suivantes s'appliquent à la fonction dans son ensemble, et décrivent comment elle se comporte ou ce qui est attendu d'être vrai.  
  
|Annotation|Description|  
|----------------|-----------------|  
|`_Called_from_function_class_(name)`|Non sauf si autonome ; au lieu de cela, il s'agit d'un attribut à utiliser avec l'annotation `_When_`.  Pour plus d'informations, consultez [Spécification du moment où une annotation est applicable et dans quel cas](../code-quality/specifying-when-and-where-an-annotation-applies.md).<br /><br /> Le paramètre `name` est une chaîne arbitraire qui apparaît dans une annotation `_Function_class_` dans la déclaration de certaines fonctions.  `_Called_from_function_class_` retourne une valeur différente de zéro si la fonction actuellement analysée est annotée à l'aide de `_Function_class_` qui a la même valeur `name`; sinon, elle retourne zéro.|  
|`_Check_return_`|Annote une valeur de retour et indique que l'appelant doit l'inspecter.  Le vérificateur signale une erreur si la fonction est appelée dans un contexte void.|  
|`_Function_class_(name)`|Le paramètre `name` est une chaîne arbitraire qui est indiquée par l'utilisateur.  Il existe dans un espace de noms qui est distinct des autres espaces de noms.  Une fonction, un pointeur de fonction, ou \(plus utilement\) un type de pointeur fonction peuvent être désignés comme appartenant à une ou plusieurs classes de fonction.|  
|`_Raises_SEH_exception_`|Annote une fonction qui déclenche toujours une exception : gestionnaire d'exceptions structuré \(SEH\) \(soumis à `_When_` et aux rapports de `_On_failure_`\).  Pour plus d'informations, consultez [Spécification du moment où une annotation est applicable et dans quel cas](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
|`_Maybe_raises_SEH_exception_`|Annote une fonction qui peut éventuellement lever une exception SEH \(soumis à `_When_` et aux rapports de `_On_failure_`\).|  
|`_Must_inspect_result_`|Annote toute valeur de sortie, notamment la valeur de retour, les paramètres, et les globals.  L'analyseur signale une erreur si la valeur de l'objet annoté n'est pas ensuite révisée. L'« inspection » inclut si elle est utilisée dans une expression conditionnelle, et est affectée à un paramètre de sortie, ou est passée comme paramètre.  Pour les valeurs de retour, `_Must_inspect_result_` implique `_Check_return_`.|  
|`_Use_decl_annotations_`|Peut être utilisé dans une définition de fonctions \(également appelé corps de la fonction\) à la place de la liste d'annotations dans l'en\-tête.  Lorsque `_Use_decl_annotations_` est utilisé, les annotations qui apparaissent dans un en\-tête de la même fonction sont utilisées comme si elles étaient également présentes dans la définition qui possède l'annotation `_Use_decl_annotations_`.|  
  
## Annotations de réussite ou échec  
 Une fonction peut échouer, et lorsque cela arrive, les résultats peuvent être incomplète ou différer du résultat attendu.  Les annotations dans la liste suivante fournissent des méthodes pour expliquer les échecs.  Pour utiliser l'une de ces annotations, vous devez leur permettre de déterminer la réussite, donc une annotation `_Success_` est requise.  Notez que `NTSTATUS` et `HRESULT` ont déjà une annotation `_Success_` intégrée à eux ; toutefois, si vous spécifiez votre propre annotation `_Success_` sur `NTSTATUS` ou `HRESULT`, elle remplace l'annotation intégrée.  
  
|Annotation|Description|  
|----------------|-----------------|  
|`_Always_(anno_list)`|De la même manière que`anno_list _On_failure_(anno_list)`; Autrement dit, les annotations dans `anno_list` s'appliquent si la fonction réussit.|  
|`_On_failure_(anno_list)`|À utiliser uniquement lorsque `_Success_` est également utilisé pour annoter la ligne explicitement ou implicitement via `_Return_type_success_` sur le typedef.  Lorsque l'annotation `_On_failure_` est présente sur un paramètre de fonction ou une valeur de retour, chaque annotation dans `anno_list` \(anno\) se comporte comme si elle avait été codé comme `_When_(!expr, anno)`, où `expr` est le paramètre de l'annotation requise `_Success_`.  Cela signifie que l'application implicite de `_Success_` à toutes les conditions après n'est pas applicable pour `_On_failure_`.|  
|`_Return_type_success_(expr)`|Peut être appliqué à un typedef.  Indique que toutes les fonctions retournant ce type n'ayant pas explicitement l'annotation `_Success_` sont annotés comme si ils avaient `_Success_(expr)`.  `_Return_type_success_` ne peut pas être utilisé sur une fonction ou un pointeur de fonction typedef.|  
|`_Success_(expr)`|`expr` est une expression qui retourne une rvalue.  Lorsque l'annotation `_Success_` est présente sur une déclaration de fonction ou une définition, chaque annotation \(`anno`.\) dans la fonction, et qui est dans la condition d'après, se comporte comme si elle était codée comme `_When_(expr, anno)`.  L'annotation `_Success_` peut uniquement être employée dans une fonction \(et non ses paramètres ou type de retour\).  Il peut y avoir au plus une annotation `_Success_` sur une fonction, et il ne peut pas être à l'intérieur d'un `_When_`, d' un `_At_`, ou d' un `_Group_`.  Pour plus d'informations, consultez [Spécification du moment où une annotation est applicable et dans quel cas](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
  
## Voir aussi  
 [Utilisation d’annotations SAL pour réduire les défauts du code C\/C\+\+](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Présentation de SAL](../code-quality/understanding-sal.md)   
 [Annotation de paramètres de fonction et valeurs de retour](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Structs et classes d’annotation](../code-quality/annotating-structs-and-classes.md)   
 [Annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md)   
 [Spécification du moment où une annotation est applicable et dans quel cas](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Fonctions intrinsèques](../code-quality/intrinsic-functions.md)   
 [Meilleures pratiques et exemples](../code-quality/best-practices-and-examples-sal.md)