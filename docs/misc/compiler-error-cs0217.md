---
title: "Erreur du compilateur CS0217 | Microsoft Docs"
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
  - "CS0217"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0217"
ms.assetid: ede61095-6e11-4f4a-8e7d-85e7a3f4fc3d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0217
Pour être applicable en tant qu’opérateur de court\-circuit, un opérateur logique défini par l’utilisateur \('operator'\) doit posséder le même type de retour que le type de ses 2 paramètres.  
  
 Si vous définissez un opérateur pour un type défini par l’utilisateur, et essayez d’utiliser l’opérateur comme opérateur de court\-circuit, l’opérateur défini par l’utilisateur doit avoir des paramètres et des valeurs de retour du même type. Pour plus d’informations sur les opérateurs de court\-circuit, consultez [&&, opérateur](/dotnet/csharp/language-reference/operators/conditional-and-operator) et [&#124;&#124;, opérateur](../Topic/%7C%7C%20Operator%20\(C%23%20Reference\).md).  
  
 L’exemple suivant génère l’erreur CS0217 :  
  
```  
// CS0217.cs using System; public class MyClass { public static bool operator true (MyClass f) { return false; } public static bool operator false (MyClass f) { return false; } public static implicit operator int(MyClass x) { return 0; } public static int operator & (MyClass f1, MyClass f2)   // CS0217 // try the following line instead // public static MyClass operator & (MyClass f1, MyClass f2) { return new MyClass(); } public static void Main() { MyClass f = new MyClass(); int i = f && f; } }  
```  
  
## Voir aussi  
 [Opérateurs surchargeables](/dotnet/csharp/programming-guide/statements-expressions-operators/overloadable-operators)