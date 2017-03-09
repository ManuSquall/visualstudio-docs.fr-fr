---
title: "Erreur du compilateur CS1520 | Microsoft Docs"
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
  - "CS1520"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1520"
ms.assetid: 1aeeee83-52a6-45dc-b197-a9a6de3a220c
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1520
La méthode doit avoir un type de retour  
  
 Une méthode qui est déclarée dans une classe, une structure ou une interface doit avoir un type de retour explicite. Dans l’exemple suivant, la méthode Square a la valeur de retour [string](/dotnet/csharp/language-reference/keywords/string) :  
  
```  
class Test { string IntToString(int i) { return i.ToString(); } }  
```  
  
 L’exemple suivant génère l’erreur CS1520 :  
  
```  
// CS1520a.cs public class x { // Method declaration missing a return type MyMethod()   // CS1520 {} // Add the desired return type: // void MyMethod2() // { } public static void Main() { } }  
```  
  
 Cette erreur peut aussi se produire quand la casse du nom d’un constructeur diffère de celle la déclaration de classe ou de struct, comme dans l’exemple suivant. Comme le nom n’est pas exactement le même que celui de la classe, le compilateur l’interprète comme une méthode normale, et non comme un constructeur, et génère l’erreur :  
  
```  
// CS1520b.cs public class Class1 { // Should be Class1, not class1 public class1()   // CS1520 { } static void Main() { } }  
```  
  
## Voir aussi  
 [Méthodes](/dotnet/csharp/programming-guide/classes-and-structs/methods)   
 [Constructeurs](/dotnet/csharp/programming-guide/classes-and-structs/constructors)