---
title: "Une valeur de type &#39;&lt;type1&gt;&#39; ne peut pas &#234;tre convertie en &#39;&lt;type2&gt;&#39; | Microsoft Docs"
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
  - "bc30311"
  - "vbc30311"
helpviewer_keywords: 
  - "BC30311"
ms.assetid: e3a513d4-2a1e-46d6-b592-b2e756b89d7d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une valeur de type &#39;&lt;type1&gt;&#39; ne peut pas &#234;tre convertie en &#39;&lt;type2&gt;&#39;
Une instruction essaie de convertir un type de données dans un autre d’une manière non définie. Cette erreur peut avoir les causes suivantes :  
  
-   Une conversion spécifie deux types de données entre lesquels il n’y a pas de conversion possible. Tel est le cas, par exemple, d’une conversion d’une valeur `Boolean` en type `Date`.  
  
-   Une initialisation de tableau ne présente pas d’accolades \(`{}`\) à la suite d’une clause `New`. Dans ce cas, \<type2\> est au format « tableau unidimensionnel de \<type\> ».  
  
 **ID d’erreur :** BC30311  
  
### Pour corriger cette erreur  
  
-   Vérifiez que l’expression peut être convertie dans le type des données de destination.  
  
-   Si \<type2\> est un tableau, vérifiez que la clause `New` contient des parenthèses et des accolades à la suite du nom de type. Le code suivant illustre l’initialisation correcte d’un tableau.  
  
    ```  
    Dim anIntArray As Integer() = New Integer() {}  
    ```  
  
## Voir aussi  
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)   
 [How to: Initialize an Array Variable in Visual Basic](../Topic/How%20to:%20Initialize%20an%20Array%20Variable%20in%20Visual%20Basic.md)