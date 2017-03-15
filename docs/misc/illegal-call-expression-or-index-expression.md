---
title: "Expression d’appel ou expression d’index non conforme | Microsoft Docs"
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
  - "vbc32303"
  - "bc32303"
helpviewer_keywords: 
  - "BC32303"
ms.assetid: eed6a16e-4a44-4f72-b1de-d4212940da37
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Expression d’appel ou expression d’index non conforme
Une valeur entre parenthèses suit une expression qui n’est pas une procédure, une propriété ni un tableau.  
  
 Le code suivant peut générer cette erreur.  
  
 `Dim testVariable As Object = Nothing(1)`  
  
 Étant donné que `Nothing` ne prend pas d’arguments ni d’index, vous ne pouvez pas l’utiliser avec des parenthèses.  
  
 **ID d’erreur :** BC32303  
  
### Pour corriger cette erreur  
  
-   Supprimez les parenthèses et les valeurs qu’elles contiennent.  
  
## Voir aussi  
 [How to: Call a Procedure That Returns a Value](../Topic/How%20to:%20Call%20a%20Procedure%20That%20Returns%20a%20Value%20\(Visual%20Basic\).md)   
 [How to: Call a Procedure that Does Not Return a Value](../Topic/How%20to:%20Call%20a%20Procedure%20that%20Does%20Not%20Return%20a%20Value%20\(Visual%20Basic\).md)   
 [NOTINBUILD Comment : placer une valeur dans un tableau](http://msdn.microsoft.com/fr-fr/6dddc79c-cf60-41c2-b572-8bfa49b4fe7e)   
 [NOTINBUILD Comment : obtenir une valeur d’un tableau](http://msdn.microsoft.com/fr-fr/202a6468-8ccb-4864-bd8b-eab3b42d4288)   
 [How to: Put a Value in a Property](../Topic/How%20to:%20Put%20a%20Value%20in%20a%20Property%20\(Visual%20Basic\).md)   
 [How to: Get a Value from a Property](../Topic/How%20to:%20Get%20a%20Value%20from%20a%20Property%20\(Visual%20Basic\).md)