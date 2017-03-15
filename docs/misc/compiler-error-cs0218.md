---
title: "Erreur du compilateur CS0218 | Microsoft Docs"
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
  - "CS0218"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0218"
ms.assetid: f675e06a-c55c-44a1-b5db-0df178fd8f79
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0218
Le type \('type'\) doit contenir les déclarations de l’opérateur true et de l’opérateur false  
  
 Si vous définissez un opérateur pour un type défini par l’utilisateur et que vous essayez ensuite d’utiliser l’opérateur comme opérateur de court\-circuit, vous devez définir les opérateurs true et false pour l’opérateur défini par l’utilisateur. Pour plus d’informations sur les opérateurs de court\-circuit, consultez [&&, opérateur](/dotnet/csharp/language-reference/operators/conditional-and-operator) et [&#124;&#124;, opérateur](../Topic/%7C%7C%20Operator%20\(C%23%20Reference\).md).  
  
 L’exemple suivant génère l’erreur CS0218 :  
  
```  
// CS0218.cs using System; public class MyClass { // uncomment these operator declarations to resolve this CS0218 /* public static bool operator true (MyClass f) { return false; } public static bool operator false (MyClass f) { return false; } */ public static implicit operator int(MyClass x) { return 0; } public static MyClass operator & (MyClass f1, MyClass f2) { return new MyClass(); } public static void Main() { MyClass f = new MyClass(); int i = f && f;   // CS0218, requires operators true and false } }  
```  
  
## Voir aussi  
 [Conversion, opérateurs](/dotnet/csharp/programming-guide/statements-expressions-operators/conversion-operators)