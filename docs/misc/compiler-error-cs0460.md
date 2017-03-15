---
title: "Erreur du compilateur CS0460 | Microsoft Docs"
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
  - "CS0460"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0460"
ms.assetid: 98d39ded-d3f9-4520-b912-892e574c056b
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0460
Les contraintes pour les méthodes d'implémentation d'interface override et explicite sont héritées de la méthode de base et ne peuvent donc pas être spécifiées directement  
  
 Quand une méthode générique qui fait partie d’une classe dérivée remplace une méthode dans la classe de base, vous ne pouvez pas spécifier de contraintes sur la méthode remplacée. La méthode de substitution dans la classe dérivée hérite ses contraintes de la méthode de la classe de base.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0460.  
  
```  
// CS0460.cs // compile with: /target:library class BaseClass { BaseClass() { } } interface I { void F1<T>() where T : BaseClass; void F2<T>() where T : struct; void F3<T>() where T : BaseClass; } class ExpImpl : I { void I.F1<T>() where T : BaseClass {}   // CS0460 void I.F2<T>() where T : class {}  // CS0460 }  
```