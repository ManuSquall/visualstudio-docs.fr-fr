---
title: "La variable de ressource &#39;Using&#39; doit avoir une initialisation explicite | Microsoft Docs"
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
  - "vbc36011"
  - "bc36011"
helpviewer_keywords: 
  - "BC36011"
ms.assetid: 5db996a6-0802-4b67-91f1-4aa9c3dd6b09
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La variable de ressource &#39;Using&#39; doit avoir une initialisation explicite
Une instruction `Using` spécifie au moins une ressource qu’elle n’initialise pas avec une clause `New`.  
  
 Si vous n’avez pas acquis la ressource avant de passer le contrôle au bloc `Using`, l’instruction `Using` doit l’acquérir. Pour ce faire, elle doit créer un objet à partir de la classe spécifiée, qui nécessite une clause `New`.  
  
 **ID d’erreur :** BC36011  
  
### Pour corriger cette erreur  
  
-   Si vous avez déjà acquis la ressource, utilisez une expression ou une variable de référence dans l’instruction `Using` qui prend la valeur de la ressource acquise.  
  
     `Dim newFont As New System.Drawing.Font`  
  
     `Using newFont`  
  
-   Si vous n’avez pas encore acquis la ressource, ajoutez une clause `New` à l’instruction `Using`.  
  
     `Using newFont as`   `New`   `System.Drawing.Font`  
  
## Voir aussi  
 [Using Statement](/dotnet/visual-basic/language-reference/statements/using-statement)   
 [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [How to: Dispose of a System Resource](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)