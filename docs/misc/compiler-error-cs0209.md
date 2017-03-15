---
title: "Erreur du compilateur CS0209 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0209"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0209"
ms.assetid: a408a869-02db-414f-97c1-bfb1637f6155
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0209
Le type des variables locales déclaré dans une instruction fixed doit être un type pointeur  
  
 La variable que vous déclarez dans une [instruction fixed](/dotnet/csharp/language-reference/keywords/fixed-statement) doit être un pointeur. Pour plus d’informations, consultez [Pointeurs et code unsafe](/dotnet/csharp/programming-guide/unsafe-code-pointers/index).  
  
 L’exemple suivant génère l’erreur CS0209 :  
  
```  
// CS0209.cs // compile with: /unsafe class Point { public int x, y; } public class MyClass { unsafe public static void Main() { Point pt = new Point(); fixed (int i)    // CS0209 { } // try the following lines instead /* fixed (int* p = &pt.x) { } fixed (int* q = &pt.y) { } */ } }  
```