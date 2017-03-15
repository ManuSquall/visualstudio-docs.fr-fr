---
title: "Erreur du compilateur CS0463 | Microsoft Docs"
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
  - "CS0463"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0463"
ms.assetid: 0cb4be4e-86ea-4ade-8817-b17d4cacd4d5
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0463
Échec de l’évaluation de l’expression de constante décimale avec l’erreur : 'error'  
  
 Cette erreur se produit quand une expression décimale de constante dépasse sa capacité au moment de la compilation.  
  
 En général, vous obtenez des erreurs de dépassement de capacité au moment de l’exécution. Dans ce cas, vous avez défini l’expression de constante d’une manière telle que le compilateur peut évaluer le résultat et savoir qu’un dépassement de capacité va se produire.  
  
## Exemple  
 Le code suivant génère l’erreur CS0463.  
  
```  
// CS0463.cs using System; class MyClass { public static void Main() { const decimal myDec = 79000000000000000000000000000.0m + 79000000000000000000000000000.0m; // CS0463 Console.WriteLine(myDec.ToString()); } }  
```