---
title: "L’op&#233;rande &#39;Is&#39; du type &#39;typename&#39; ne peut &#234;tre compar&#233; qu’&#224; &#39;Nothing&#39;, car &#39;typename&#39; est un type nullable | Microsoft Docs"
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
  - "vbc32127"
  - "bc32127"
helpviewer_keywords: 
  - "BC32127"
ms.assetid: 68b745b5-8605-4bf3-a6ec-69e67b3cff2d
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’op&#233;rande &#39;Is&#39; du type &#39;typename&#39; ne peut &#234;tre compar&#233; qu’&#224; &#39;Nothing&#39;, car &#39;typename&#39; est un type nullable
Une variable déclarée comme nullable a été comparée à une expression autre que `Nothing` à l’aide de l’opérateur `Is`.  
  
 **ID d’erreur :** BC32127  
  
### Pour corriger cette erreur  
  
1.  Pour comparer un type nullable à une expression autre que `Nothing` à l’aide de l’opérateur `Is`, appelez la méthode `GetType` sur le type nullable et comparez le résultat à l’expression, comme illustré dans l’exemple suivant.  
  
    ```vb#  
    Dim number? As Integer = 5 If number IsNot Nothing Then If number.GetType() Is Type.GetType("System.Int32") Then End If End If  
    ```  
  
## Voir aussi  
 [Nullable Value Types](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)   
 [Is Operator](/dotnet/visual-basic/language-reference/operators/is-operator)