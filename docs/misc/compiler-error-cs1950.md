---
title: "Erreur du compilateur&#160;CS1950 | Microsoft Docs"
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
  - "CS1950"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1950"
ms.assetid: e37fb5b1-09e0-47a6-9db5-a48f90ea7bbb
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur&#160;CS1950
La méthode Add surchargée 'nom' correspondant le mieux à l’initialiseur de collection a des arguments non valides.  
  
 Pour prendre en charge les initialiseurs de collection, une classe doit implémenter IEnumerable et avoir une méthode `Add` publique. Pour initialiser le type à l’aide d’un initialiseur de collection, le paramètre d’entrée de la méthode `Add` doit être compatible avec le type de l’objet que vous essayez d’ajouter.  
  
### Pour corriger cette erreur  
  
-   Utilisez un type compatible dans l’initialiseur de collection.  
  
-   Modifiez le paramètre d’entrée et\/ou l’accessibilité de la méthode `Add` dans le type de collection.  
  
-   Ajoutez une nouvelle méthode `Add` avec un paramètre d’entrée qui correspond à ce que vous passez.  
  
-   Faites de votre classe de collection une classe générique de sorte qu’elle puisse avoir une méthode `Add` qui accepte le type que vous passez.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1950 :  
  
```  
// cs1950.cs using System.Collections; class TestClass : CollectionBase { public void Add(int c) { } } class Test { static void Main() { TestClass t = new TestClass { "hi" }; // CS1950 } }  
```  
  
## Voir aussi  
 [Initialiseurs d'objets et de collections](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)