---
title: "Erreur du compilateur CS0763 | Microsoft Docs"
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
  - "CS0763"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0763"
ms.assetid: 940870ba-1250-4365-acaa-7f968ee96c5b
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0763
Soit les deux déclarations de méthode partielles sont statiques, soit aucune ne l’est.  
  
 Une déclaration de méthode partielle ne peut pas avoir une partie statique et une autre qui ne l’est pas.  
  
### Pour corriger cette erreur  
  
1.  Faites en sorte que les parties soient toutes les deux statiques ou toutes les deux non statiques.  
  
## Exemple  
 Le code suivant génère l’erreur CS0763 :  
  
```  
// cs0763.cs using System; public partial class C { static partial void Part(); partial void Part() // CS0763 { } public static int Main() { return 1; } }  
```  
  
## Voir aussi  
 [Classes et méthodes partielles](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [statiques](/dotnet/csharp/language-reference/keywords/static)