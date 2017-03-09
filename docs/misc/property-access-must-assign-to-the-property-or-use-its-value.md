---
title: "Un acc&#232;s &#224; la propri&#233;t&#233; doit assigner la propri&#233;t&#233; ou utiliser sa valeur | Microsoft Docs"
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
  - "bc30545"
  - "vbc30545"
helpviewer_keywords: 
  - "BC30545"
ms.assetid: df271c05-1e7a-44e8-bf53-79f06ef916ab
caps.latest.revision: 11
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Un acc&#232;s &#224; la propri&#233;t&#233; doit assigner la propri&#233;t&#233; ou utiliser sa valeur
Vous avez tenté d’accéder à une propriété sans lui assigner de valeur ou sans utiliser sa valeur. Le code suivant est fourni à titre d'exemple :  
  
 [!CODE [VbVbalrErrorSamples#1](VbVbalrErrorSamples#1)]  
  
 **ID d’erreur :** BC30545  
  
### Pour corriger cette erreur  
  
-   Assignez une valeur à la propriété, comme illustré dans l’exemple suivant :  
  
     [!CODE [VbVbalrErrorSamples#3](VbVbalrErrorSamples#3)]  
  
     ou  
  
-   Utilisez la valeur de la propriété, comme illustré dans l’exemple suivant :  
  
     [!CODE [VbVbalrErrorSamples#2](VbVbalrErrorSamples#2)]  
  
## Voir aussi  
 [Procédures de propriété](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Assignment Operators](/dotnet/visual-basic/language-reference/operators/assignment-operators)