---
title: "Avertissement du compilateur (niveau&#160;2) CS0251 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0251"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0251"
ms.assetid: 791a325a-096d-4d87-b31d-d9b3124210c8
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;2) CS0251
Indexation d’un tableau avec un index négatif \(les index de tableau commencent toujours à zéro\)  
  
 N’utilisez pas un nombre négatif pour indexer dans un tableau.  
  
 L’exemple suivant génère l’avertissement CS0251 :  
  
```  
// CS0251.cs // compile with: /W:2 class MyClass { public static void Main() { int[] myarray = new int[] {1,2,3}; try { myarray[-1]++;   // CS0251 // try the following line instead // myarray[1]++; } catch (System.IndexOutOfRangeException e) { System.Console.WriteLine("{0}", e); } } }  
```