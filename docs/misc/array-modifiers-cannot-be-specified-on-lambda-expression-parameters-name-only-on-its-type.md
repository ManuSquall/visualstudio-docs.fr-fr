---
title: "Les modificateurs de tableau ne peuvent pas &#234;tre sp&#233;cifi&#233;s sur le nom des param&#232;tres de l’expression lambda, uniquement sur son type | Microsoft Docs"
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
  - "vbc36643"
  - "bc36643"
helpviewer_keywords: 
  - "BC36643"
ms.assetid: 34b6141b-6eab-4641-a3f4-53ef28c1792b
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les modificateurs de tableau ne peuvent pas &#234;tre sp&#233;cifi&#233;s sur le nom des param&#232;tres de l’expression lambda, uniquement sur son type
Des arguments de tableau peuvent être envoyés à des expressions lambda, mais la déclaration de paramètre doit inclure le type d’élément.  
  
```vb#  
' Not valid.  
' Dim arrayExample1 = Function(arrayPara()) 2  
  
' Valid.  
Dim arrayExample2 = Function(arrayPara() As Integer) arrayPara.Length > 0  
Dim arrayexample3 = Function(arrayPara As Integer()) arrayPara.Length > 0  
```  
  
 **ID d’erreur :** BC36643  
  
### Pour corriger cette erreur  
  
-   Spécifiez le type des éléments dans le paramètre de tableau.  
  
## Voir aussi  
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)