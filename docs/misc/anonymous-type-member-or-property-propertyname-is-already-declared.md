---
title: "Le membre de type anonyme ou la propri&#233;t&#233; &#39;&lt;nom_propri&#233;t&#233;&gt;&#39; est d&#233;j&#224; d&#233;clar&#233; | Microsoft Docs"
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
  - "bc36547"
  - "vbc36547"
helpviewer_keywords: 
  - "BC36547"
ms.assetid: 4c60d24a-62d7-404a-bc35-d1a1d9c9f851
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le membre de type anonyme ou la propri&#233;t&#233; &#39;&lt;nom_propri&#233;t&#233;&gt;&#39; est d&#233;j&#224; d&#233;clar&#233;
Un nom de propriété ne peut être établi qu’une seule fois dans la déclaration d’un type anonyme. Par exemple, les déclarations suivantes ne sont pas valides :  
  
```vb#  
'' Not valid, because the Label property is assigned to twice.  
' Dim anonType1 = New With {.Label = "Debra Garcia", .Label = .Label & ", President"}  
'' Not valid, because the property name inferred for both properties is  
'' Name.  
' Dim anonType2 = New With {Key product.Name, Key car1.Name}  
```  
  
 **ID d’erreur :** BC36547  
  
### Pour corriger cette erreur  
  
-   Utilisez un nom différent pour l’une des propriétés.  
  
    ```vb#  
    ' Valid.  
    Dim anonType3 = New With {.Name = "Debra Garcia", .Label = .Name & ", President"}  
    ```  
  
-   Attribuez de nouveaux noms aux variables et aux propriétés à partir desquelles vous déduisez des noms et des valeurs.  
  
    ```vb#  
    ' Valid.  
    Dim anonType4 = New With {Key .ProductName = product.Name, Key .CarName = car1.Name}  
  
    ```  
  
## Voir aussi  
 [Anonymous Types](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [Comment : déduire les types et les noms de propriétés dans des déclarations de types anonymes](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)