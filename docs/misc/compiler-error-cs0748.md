---
title: "Erreur du compilateur CS0748 | Microsoft Docs"
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
  - "CS0748"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0748"
ms.assetid: da1935af-a5ea-41f4-84ae-58559b750566
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0748
Utilisation du paramètre lambda incohérente ; les types de paramètres doivent être tous explicites ou tous implicites.  
  
 Si une expression lambda a plusieurs paramètres d’entrée, certains paramètres ne peuvent pas utiliser un typage implicite tandis que d’autres utilisent un typage explicite.  
  
### Pour corriger cette erreur  
  
1.  Donnez à tous les paramètres d’entrée des types implicites ou des types explicites.  
  
## Exemple  
 Le code suivant génère l’erreur CS0748 car, dans l’expression lambda, seul `alpha` reçoit un type explicite :  
  
```  
// cs0748.cs class CS0748 { delegate double D(int x, int y); D d = (int alpha, beta) => { return beta / alpha; }; // CS0748 }  
```  
  
## Voir aussi  
 [Expressions lambda](/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions)