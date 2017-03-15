---
title: "Le nom du champ ou de la propri&#233;t&#233; initialis&#233; doit commencer par &#39;.&#39; | Microsoft Docs"
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
  - "vbc30985"
  - "bc30985"
helpviewer_keywords: 
  - "BC30985"
ms.assetid: 4cb543e1-477c-429c-82df-541ebff08543
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le nom du champ ou de la propri&#233;t&#233; initialis&#233; doit commencer par &#39;.&#39;
Chaque initialiseur de membre d’une liste d’initialiseurs d’objet spécifie le nom d’un champ ou d’une propriété et sa valeur initiale. Le nom du champ ou de la propriété doit être précédé d’un point. Par exemple, la déclaration suivante affecte la valeur initiale « Microsoft » à la propriété `Name` de `client`.  
  
```  
Dim client As New Customer() With { .Name = "Microsoft" }  
```  
  
 **ID d’erreur :** BC30985  
  
### Pour corriger cette erreur  
  
-   Précédez chaque nom de membre d’un point.  
  
## Voir aussi  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [NOT IN BUILD : Procédures de propriété et champs](http://msdn.microsoft.com/fr-fr/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)