---
title: "Erreur du compilateur&#160;CS1102 | Microsoft Docs"
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
  - "CS1102"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1102"
ms.assetid: 7de798d4-1b4b-4842-ae43-9bc83e6dc9a3
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur&#160;CS1102
Le modificateur de paramètre 'out' ne peut pas être utilisé avec 'this'  
  
 Quand le mot\-clé `this` modifie le premier paramètre d’une méthode statique, il signale au compilateur que la méthode est une méthode d’extension. Aucun autre modificateur n’est nécessaire ni autorisé sur le premier paramètre d’une méthode d’extension.  
  
### Pour corriger cette erreur  
  
1.  Supprimez les modificateurs non autorisés du premier paramètre.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1102 :  
  
```  
// cs1102.cs // Compile with: /target:library. public static class Extensions { // No type parameters. public static void Test(this out int i) {} // CS1102 //Single type parameter public static void Test<T>(this out T t) {}// CS1102 //Multiple type parameters public static void Test<T,U,V>(this out U u) {}// CS1102 }  
```  
  
## Voir aussi  
 [Méthodes d'extension](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)   
 [this](/dotnet/csharp/language-reference/keywords/this)   
 [out](/dotnet/csharp/language-reference/keywords/out)