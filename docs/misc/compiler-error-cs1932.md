---
title: "Erreur du compilateur CS1932 | Microsoft Docs"
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
  - "CS1932"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1932"
ms.assetid: fc927899-2d35-4d47-9ae9-8fc99295bb66
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1932
Impossible d’assigner 'expression' à une variable de portée.  
  
 Le compilateur doit pouvoir déduire le type d’une variable de portée, qu’elle soit introduite dans une clause `from` ou une clause `let`. Elle ne peut pas être null, car la valeur null n’est pas un type, et elle ne peut pas être assignée avec une expression de type unsafe.  
  
### Pour corriger cette erreur  
  
-   Supprimez l’assignation qui n’est pas valide.  
  
-   Effectuez un cast explicite de l’expression vers un type autorisé.  
  
## Exemple  
 Le code suivant génère l’erreur CS1932, car le type de la variable de portée ne peut pas être déduit. Effectuez un cast de la valeur vers le type prévu pour corriger l’erreur, comme illustré dans l’exemple suivant.  
  
```  
// CS1932.cs using System.Linq; class Test { static void Main() { var x = from i in Enumerable.Range(1, 100) let k = null // CS1932 // Try the following line instead. let k = (string) null select i; } }  
```  
  
## Voir aussi  
 [Expressions de requête \(LINQ\)](/dotnet/csharp/programming-guide/linq-query-expressions/index)