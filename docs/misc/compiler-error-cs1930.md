---
title: "Erreur du compilateur CS1930 | Microsoft Docs"
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
  - "CS1930"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1930"
ms.assetid: d28d2334-825c-4ffc-b9e9-f5d61f44d672
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1930
La variable de portée 'nom' a déjà été déclarée  
  
 La variable de portée d’une expression de requête est comprise dans la portée jusqu’à la fin de l’expression de requête. Elle doit donc avoir un identificateur unique.  
  
### Pour corriger cette erreur  
  
1.  Attribuez un nom unique à chaque variable de portée d’une expression de requête.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1930, car l’identificateur `num` est utilisé pour la variable de portée dans la clause `from` et pour la variable de portée ajoutée par la clause `let`.  
  
```  
// cs1930.cs using System.Linq; class Program { static void Main() { int[] nums = { 0, 1, 2, 3, 4, 5 }; var query = from num in nums let num = 3 // CS1930 select num; } }  
```  
  
## Voir aussi  
 [Expressions de requête \(LINQ\)](/dotnet/csharp/programming-guide/linq-query-expressions/index)