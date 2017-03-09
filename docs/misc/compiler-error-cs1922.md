---
title: "Erreur du compilateur CS1922 | Microsoft Docs"
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
  - "CS1922"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1922"
ms.assetid: a4098a25-6581-4966-b61d-318cd12f76d3
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1922
Impossible d’initialiser un type 'type' avec un initialiseur de collection, car il n’implémente pas 'System.Collections.IEnumerable'  
  
 Pour utiliser un initialiseur de collection avec un type, le type doit implémenter `IEnumerable`. Cette erreur peut se produire si vous utilisez une syntaxe d’initialiseur de collection alors que vous voulez utiliser un initialiseur d’objet.  
  
### Pour corriger cette erreur  
  
-   Si le type ne représente pas une collection, utilisez la syntaxe d’initialisation d’objet au lieu de la syntaxe d’initialiseur de collection.  
  
-   Si le type ne représente pas une collection, modifiez\-le pour qu’il implémente `IEnumerable`. Vous pourrez ensuite utiliser des initialiseurs de collection pour initialiser les objets de ce type.  
  
-   Si le type représente une collection et si vous n’avez pas accès au code source, initialisez ses éléments à l’aide de leurs constructeurs de classe ou d’autres méthodes d’initialisation.  
  
## Exemple  
 Le code suivant génère l’erreur CS1922 :  
  
```  
// cs1922.cs public class Test { public static void Main() { // Collection initializer. var tc = new TestClass  {1,"hello"} ; // CS1922 // Object initalizer. var tc2 = new TestClass { memberA = 1, memberB = "hello" }; // OK } } public class TestClass { public int memberA { get; set; } public string memberB { get; set; } }  
  
```  
  
## Voir aussi  
 [Initialiseurs d'objets et de collections](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)