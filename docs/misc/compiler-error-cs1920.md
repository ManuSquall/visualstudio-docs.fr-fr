---
title: "Erreur du compilateur&#160;CS1920 | Microsoft Docs"
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
  - "CS1920"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1920"
ms.assetid: efb4782f-a222-4fb5-9e79-8bd2d380520b
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur&#160;CS1920
L’initialiseur d’élément ne peut pas être vide.  
  
 Un initialiseur de collection est constitué d’une séquence d’initialiseurs d’éléments. Les initialiseurs d’éléments n’ont pas à être placés entre accolades sauf s’ils contiennent une expression d’assignation. Toutefois, si vous fournissez des accolades, elles ne peuvent pas être vides. Si l’initialiseur d’élément est un initialiseur d’objet, les accolades peuvent être vides tant que l’initialiseur contient une nouvelle expression de création d’objet.  
  
### Pour corriger cette erreur  
  
-   Ajoutez l’expression manquante entre les accolades.  
  
-   Si l’expression est destinée à être un initialiseur d’objet, ajoutez la nouvelle expression de création d’objet devant les accolades.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1920 :  
  
```  
// cs1920.cs using System.Collections.Generic; public class Test { public static int Main() { // Error. Empty initializer // for inner list. List<List<int>> collection = new List<List<int>>() { { } }; // CS1920 // OK. No initializer for inner list. List<List<int>> collection2 = new List<List<int>>() {  }; // OK. Inner list is initialized // to one List<int> with zero elements. List<List<int>> collection3 = new List<List<int>>() { new List<int> { } }; return 0; } }  
```  
  
## Voir aussi  
 [Initialiseurs d'objets et de collections](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)