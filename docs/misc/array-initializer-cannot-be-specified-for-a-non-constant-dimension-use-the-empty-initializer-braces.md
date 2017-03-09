---
title: "Un initialiseur de tableau ne peut pas &#234;tre sp&#233;cifi&#233; pour une dimension non constante&#160;; utilisez l’initialiseur vide &#39;{}&#39; | Microsoft Docs"
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
  - "vbc30949"
  - "bc30949"
helpviewer_keywords: 
  - "BC30949"
ms.assetid: b3d27d9c-7a1f-4bac-ad71-388b24b807b3
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Un initialiseur de tableau ne peut pas &#234;tre sp&#233;cifi&#233; pour une dimension non constante&#160;; utilisez l’initialiseur vide &#39;{}&#39;
Un tableau initialise une dimension qui n’est pas connue au moment de la compilation.  
  
 Le code suivant génère cette erreur.  
  
```  
Dim j As Integer Dim intArray As Integer = New Integer(1, j) {{0, 100}, {1,101}}  
```  
  
 Le code suivant permet d’éviter cette erreur.  
  
```  
Dim intArray As Integer = New Integer(1, j) {} For i As Integer = 0 To j intArray(0, i) = i intArray(1, i) = 100 + i Next i  
```  
  
 **ID d’erreur :** BC30949  
  
### Pour corriger cette erreur  
  
-   Si possible, spécifiez une dimension constante dans la déclaration de tableau.  
  
-   Si vous ne pouvez pas spécifier de dimension constante, vous devez initialiser le tableau à l’aide d’une boucle lorsque la dimension non constante devient connue.  
  
## Voir aussi  
 [For Each...Next, instruction](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)   
 [NOTINBUILD Vue d’ensemble des tableaux en Visual Basic](http://msdn.microsoft.com/fr-fr/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [How to: Initialize an Array Variable in Visual Basic](../Topic/How%20to:%20Initialize%20an%20Array%20Variable%20in%20Visual%20Basic.md)   
 [NOTINBUILD Procédure : initialisation d’un tableau multidimensionnel](http://msdn.microsoft.com/fr-fr/502dcf8b-d86c-46f1-ad7d-3ce809645774)