---
title: "Erreur du compilateur CS0156 | Microsoft Docs"
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
  - "CS0156"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0156"
ms.assetid: 32026b1b-bcd7-4464-b63f-3b38c00452a6
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0156
Une instruction throw sans argument n'est pas autorisée dans une clause finally qui est imbriquée dans la clause catch englobante la plus proche  
  
 Une instruction [throw](/dotnet/csharp/language-reference/keywords/throw) sans paramètre peut uniquement apparaître dans une clause **catch** qui n’accepte aucun paramètre.  
  
 Pour plus d’informations, consultez [Instructions de gestion des exceptions](/dotnet/csharp/language-reference/keywords/exception-handling-statements) et [Exceptions et gestion des exceptions](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling).  
  
 L’exemple suivant génère l’erreur CS0156 :  
  
```  
// CS0156.cs using System; namespace MyNamespace { public class MyClass2 : Exception { } public class MyClass { public static void Main() { try { throw;   // CS0156 } catch(MyClass2) { throw;   // this throw is valid } } } }  
```