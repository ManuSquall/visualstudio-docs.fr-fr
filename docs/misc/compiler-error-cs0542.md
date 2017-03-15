---
title: "Erreur du compilateur CS0542 | Microsoft Docs"
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
  - "CS0542"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0542"
ms.assetid: 68a89948-8b56-4cd5-95e2-0df7fcad50ac
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0542
'user\-defined type' : les noms de membres doivent être différents de leur type englobant  
  
 Les membres d’une classe ou d’un struct ne peuvent pas porter le même nom que la classe ou le struct, sauf s’ils sont des constructeurs.  
  
 L’exemple suivant génère l’erreur CS0542 :  
  
```c#  
// CS0542.cs class C { public int C; }  
```  
  
 Cette erreur peut se produire si vous placez par inadvertance un type de retour sur un constructeur, ce qui en fait une méthode ordinaire. L’exemple suivant génère l’erreur CS0542 parce que `F` est une méthode, et non pas un constructeur, puisqu’elle a un type de retour :  
  
```c#  
// CS0542.cs class F { // Remove void from F() to resolve the problem. void F()   // CS0542, same name as the class { } } class MyClass { public static void Main() { } }  
```  
  
 Si votre classe est nommée 'Item' et a un indexeur déclaré en tant que `this`, cette erreur peut se produire. Un indexeur par défaut porte le nom 'Item' dans le code émis, ce qui crée le conflit.  
  
```c#  
// CS0542b.cs class Item { public int this[int i]  // CS0542 { get { return 0; } } } class CMain { public static void Main() { } }  
```