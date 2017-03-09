---
title: "Erreur du compilateur CS1953 | Microsoft Docs"
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
  - "CS1953"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1953"
ms.assetid: b8af5eed-0f3b-4258-b4e2-f5d184288239
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1953
Une arborescence de l’expression lambda ne peut pas contenir un groupe de méthodes.  
  
 Un appel de méthode nécessite l’opérateur `()`. Le nom de la méthode sans cet opérateur fait référence au groupe de méthodes, qui est l’ensemble de toutes les méthodes surchargées portant ce nom.  
  
### Pour corriger cette erreur  
  
1.  Si vous souhaitez appeler la méthode, ajoutez l’opérateur `()`.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1953 :  
  
```  
// cs1953.cs using System; using System.Linq.Expressions; class CS1953 { public static void Main() { double num = 10; Expression<Func<bool>> testExpr = () => num.GetType is int; // CS1953 } }  
```