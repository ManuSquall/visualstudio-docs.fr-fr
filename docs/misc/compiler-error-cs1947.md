---
title: "Erreur du compilateur CS1947 | Microsoft Docs"
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
  - "CS1947"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1947"
ms.assetid: e2822fba-a176-4466-9cdc-63c44e22ebcb
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1947
La variable de portée 'nom de variable' ne peut pas être assignée à \-\- elle est en lecture seule  
  
 Une variable de portée est semblable à une variable d’itération d’une instruction `foreach`. Elle ne peut pas être assignée dans une expression de requête.  
  
### Pour corriger cette erreur  
  
1.  Supprimez l’assignation à la variable de portée.  
  
2.  Si nécessaire, ajoutez une nouvelle variable de portée à l’aide de la clause `let`, puis utilisez\-la pour stocker la valeur.  
  
## Exemple  
 Le code suivant génère l’erreur CS1947 :  
  
```  
// cs1947.cs using System.Linq; class Test { static void Main() { int[] array = new int[] { 1, 2, 3, 4, 5 }; var x = from i in array let k = i select i = 5; // CS1947 x.ToList(); } }  
```  
  
## Voir aussi  
 [Expressions de requête \(LINQ\)](/dotnet/csharp/programming-guide/linq-query-expressions/index)