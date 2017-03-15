---
title: "Erreur du compilateur&#160;CS1945 | Microsoft Docs"
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
  - "CS1945"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1945"
ms.assetid: 787f61b0-4767-451c-8c78-8e456b5057eb
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur&#160;CS1945
Une arborescence de l’expression ne peut pas contenir une expression de méthode anonyme.  
  
 Les arborescences d’expression peuvent contenir uniquement des expressions. Les méthodes anonymes peuvent représenter uniquement des instructions.  
  
### Pour corriger cette erreur  
  
1.  N’essayez pas de créer une arborescence d’expression avec une instruction.  
  
## Exemple  
 Le code suivant génère l’erreur CS1945 :  
  
```  
// cs1945.cs using System; using System.Linq.Expressions; public delegate void D(); class Test { static void Main() { Expression<Func<int, Func<int, bool>>> tree = (x => delegate(int i) { return true; }); // CS1945 } }  
```  
  
## Voir aussi  
 [Arborescences d'expression](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)   
 [Instructions, expressions et opérateurs](/dotnet/csharp/programming-guide/statements-expressions-operators/index)