---
title: "Erreur du compilateur CS1952 | Microsoft Docs"
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
  - "CS1952"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1952"
ms.assetid: 8c560bf9-df93-40f5-a3d8-c66b31cde08f
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1952
Une arborescence de l'expression lambda ne peut pas contenir une méthode avec des arguments de variables  
  
 Le mot clé `__arglist` non pris en charge n’est pas autorisé dans les expressions lambda qui sont compilées en arborescences d’expression.  
  
### Pour corriger cette erreur  
  
1.  Oubliez tout simplement `__arglist`.  
  
## Exemple  
 Le code suivant génère l’erreur CS1952 :  
  
```  
// cs1952.cs using System; using System.Linq.Expressions; class Test { public static int M(__arglist) { return 1; } static int Main() { Expression<Func<int, int>> f = x => Test.M(__arglist(x)); // CS1952 return 1; } }  
  
```