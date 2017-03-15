---
title: "Erreur du compilateur CS1931 | Microsoft Docs"
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
  - "CS1931"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1931"
ms.assetid: c0071c3d-ae11-4073-87df-508150daef68
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1931
La variable de portée 'variable' est en conflit avec une déclaration précédente de 'variable'.  
  
 La déclaration d’une variable de portée, comme toute autre déclaration, doit avoir un identificateur unique au sein de l’espace de déclaration de la variable.  
  
### Pour corriger cette erreur  
  
1.  Donnez un nom unique à la variable de portée.  
  
## Exemple  
 Le code suivant génère l’erreur CS1931, car l’identificateur `x` est utilisé à la fois en tant que variable locale dans `Main` et en tant que variable de portée dans l’expression de requête :  
  
```  
// cs1931.cs class Test { static void Main() { int x = 1; var y = from x in Enumerable.Range(1, 100) // CS1931 select x; } }  
```  
  
## Voir aussi  
 [Expressions de requête \(LINQ\)](/dotnet/csharp/programming-guide/linq-query-expressions/index)