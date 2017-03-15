---
title: "&#39;Equals&#39; ne peut pas comparer une valeur de type &lt;type1&gt; &#224; une valeur de type &lt;type2&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36621"
  - "bc36621"
helpviewer_keywords: 
  - "BC36621"
ms.assetid: bd40bf57-3a12-407a-8622-7e428850c77c
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Equals&#39; ne peut pas comparer une valeur de type &lt;type1&gt; &#224; une valeur de type &lt;type2&gt;
Un opérateur `Equals` dans une clause `Join` ou `Group Join` a tenté de comparer un type de données à un autre d’une manière qui n’est pas définie. Une comparaison entre une valeur `Boolean` et un type `Date` en est un exemple.  
  
 **ID d’erreur :** BC36621  
  
### Pour corriger cette erreur  
  
-   Vérifiez que les valeurs situées de chaque côté de l’opérateur `Equals` peuvent être converties en un type de données commun. Pour accomplir cette tâche, plusieurs options s’offrent à vous :  
  
    -   Utilisez la fonction `CType` pour convertir une ou plusieurs valeurs en un type spécifique.  
  
    -   Utilisez des méthodes de conversion ou la classe <xref:System.Convert> pour convertir une ou plusieurs des valeurs en un type commun immuable.  
  
    -   Convertissez les valeurs de chaînes à l’aide de la méthode `ToString`.  
  
## Voir aussi  
 [CType, fonction](/dotnet/visual-basic/language-reference/functions/ctype-function)   
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)   
 [Join Clause](/dotnet/visual-basic/language-reference/queries/join-clause)   
 [Group Join Clause](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)