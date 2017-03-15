---
title: "Erreur du compilateur CS0035 | Microsoft Docs"
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
  - "CS0035"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0035"
ms.assetid: a622113e-98a4-4583-992c-1fb55139320a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0035
L’opérateur 'opérateur' est ambigu pour un opérande de type 'type'  
  
 Plusieurs conversions sont disponibles et le compilateur ne sait pas laquelle choisir avant d’appliquer l’opérateur. Pour plus d’informations, consultez [Conversions définies par l'utilisateur basées sur un modèle](../misc/templated-user-defined-conversions.md) et [Conversion, opérateurs](/dotnet/csharp/programming-guide/statements-expressions-operators/conversion-operators).  
  
 L’exemple suivant génère l’erreur CS0035 :  
  
```  
// CS0035.cs class MyClass { private int i; public MyClass(int i) { this.i = i; } public static implicit operator double(MyClass x) { return (double) x.i; } public static implicit operator decimal(MyClass x) { return (decimal) x.i; } } class MyClass2 { static void Main() { MyClass x = new MyClass(7); object o = - x;   // CS0035 // try a cast: // object o = - (double)x; } }  
  
```