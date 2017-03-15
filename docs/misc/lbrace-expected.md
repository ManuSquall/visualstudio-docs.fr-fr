---
title: "&#39;{&#39; attendu | Microsoft Docs"
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
  - "vbc30987"
  - "bc30987"
helpviewer_keywords: 
  - "BC30987"
ms.assetid: 3d1552b6-338a-47cf-84d5-77b59209e0d3
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;{&#39; attendu
Pour déclarer une instance d’un type nommé ou anonyme à l’aide d’un initialiseur d’objet, vous devez placer la liste des champs ou des propriétés et leurs valeurs initiales entre accolades \({et}\).  
  
```  
Dim client As New Customer() With {.Name = "Microsoft", .City = "Seattle"}  
Dim emp = New Employee() With {.Name = "Rob Young", .ID = 55555}  
Dim anon = New With {.ID = 123456}  
```  
  
 **ID d’erreur :** BC30987  
  
### Pour corriger cette erreur  
  
-   Après `With`, ajoutez une liste d’initialisation entre accolades.  
  
## Voir aussi  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [NOT IN BUILD : Procédures de propriété et Champs](http://msdn.microsoft.com/fr-fr/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)   
 [Anonymous Types](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)