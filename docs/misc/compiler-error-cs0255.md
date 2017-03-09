---
title: "Erreur du compilateur CS0255 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0255"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0255"
ms.assetid: b45f5d5a-1923-4fe1-a858-e5ef5590a108
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0255
stackalloc ne peut être utilisé dans un bloc catch ou finally  
  
 Vous ne pouvez pas utiliser le mot clé [stackalloc](/dotnet/csharp/language-reference/keywords/stackalloc) dans un bloc [catch](/dotnet/csharp/language-reference/keywords/try-catch) ou [finally](/dotnet/csharp/language-reference/keywords/try-catch-finally). Pour plus d'informations, consultez [Exceptions et gestion des exceptions](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling).  
  
 L’exemple suivant génère l’erreur CS0255 :  
  
```  
// CS0255.cs // compile with: /unsafe using System; public class TestTryFinally { public static unsafe void Test() { int i = 123; string s = "Some string"; object o = s; try { // Conversion is not valid; o contains a string not an int i = (int) o; } finally { Console.Write("i = {0}", i); int* fib = stackalloc int[100];   // CS0255 } } public static void Main() { } }  
```