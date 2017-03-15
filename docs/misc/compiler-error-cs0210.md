---
title: "Erreur du compilateur CS0210 | Microsoft Docs"
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
  - "CS0210"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0210"
ms.assetid: 9f2ec1b8-6ca4-4147-b004-e3b43e7e8754
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0210
Vous devez fournir un initialiseur dans une déclaration d'instruction fixed ou using  
  
 Vous devez déclarer et initialiser la variable dans une [instruction fixed](/dotnet/csharp/language-reference/keywords/fixed-statement). Pour plus d’informations, consultez [Pointeurs et code unsafe](/dotnet/csharp/programming-guide/unsafe-code-pointers/index).  
  
 L’exemple suivant génère l’erreur CS0210 :  
  
```  
// CS0210a.cs // compile with: /unsafe class Point { public int x, y; } public class MyClass { unsafe public static void Main() { Point pt = new Point(); fixed (int i)    // CS0210 { } // try the following lines instead /* fixed (int* p = &pt.x) { } fixed (int* q = &pt.y) { } */ } }  
```  
  
 L’exemple suivant génère également l’erreur CS0210, car l’[instruction using](/dotnet/csharp/language-reference/keywords/using-statement) n’a pas d’initialiseur.  
  
```  
// CS0210b.cs using System.IO; class Test { static void Main() { using (StreamWriter w) // CS0210 // Try this line instead: // using (StreamWriter w = new StreamWriter("TestFile.txt")) { w.WriteLine("Hello there"); } } }  
```