---
title: "Type ou &#39;With&#39; attendu | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30988"
  - "bc30988"
helpviewer_keywords: 
  - "BC30988"
ms.assetid: ab9c0cee-9fe4-4764-a3c2-aec16e709d4c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Type ou &#39;With&#39; attendu
Quand vous déclarez une instance de classe, le mot clé `New` doit être suivi d’un nom de type ou de `With`. Par exemple, les instructions suivantes déclarent chacune `client` comme étant une instance de la classe `Customer`. Le nom de type `Customer` suit `New`.  
  
```  
' Dim client As New Customer()  
' The next declaration uses an object initializer.  
Dim client As New Customer() With {.Name = "Litware, Inc."}  
```  
  
 À partir de [!INCLUDE[vb_orcas_long](../misc/includes/vb_orcas_long_md.md)], vous pouvez déclarer un objet comme étant une instance d’un type anonyme, auquel cas vous ne spécifiez pas de type de données. Dans les déclarations de type anonyme, le mot clé `With` suit `New`.  
  
```  
Dim person = New With {.Name ="Mike Nash", .Age = 27}  
```  
  
 **ID d’erreur :** BC30988  
  
### Pour corriger cette erreur  
  
-   Modifiez la déclaration de sorte que `With` ou un nom de type suive `New`.  
  
## Voir aussi  
 [Anonymous Types](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [NotInBuild : Instructions de déclaration en Visual Basic](http://msdn.microsoft.com/fr-fr/81f3c398-f45c-4d95-80bf-aa39d1a0fb30)