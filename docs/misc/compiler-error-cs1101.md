---
title: "Erreur du compilateur&#160;CS1101 | Microsoft Docs"
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
  - "CS1101"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1101"
ms.assetid: d6fc8834-eadf-4497-b442-0751895e6764
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur&#160;CS1101
Le modificateur de paramètre 'ref' ne peut pas être utilisé avec 'this'.  
  
 Lorsque le mot\-clé `this` modifie le premier paramètre d’une méthode statique, il signale au compilateur que la méthode est une méthode d’extension. Aucun autre modificateur n’est nécessaire ou autorisé sur le premier paramètre d’une méthode d’extension.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1101 :  
  
```  
// cs1101.cs // Compile with: /target:library public static class Extensions { // No type parameters. public static void Test(ref this int i) {} // CS1101 // Single type parameter. public static void Test<T>(ref this T t) {}// CS1101 // Multiple type parameters. public static void Test<T,U,V>(ref this U u) {}// CS1101 }  
```  
  
## Voir aussi  
 [Méthodes d'extension](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)   
 [this](/dotnet/csharp/language-reference/keywords/this)   
 [ref](/dotnet/csharp/language-reference/keywords/ref)