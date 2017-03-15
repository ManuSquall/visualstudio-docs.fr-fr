---
title: "Erreur du compilateur CS0756 | Microsoft Docs"
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
  - "CS0756"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0756"
ms.assetid: 847b20b0-bbf0-43a2-8728-4b54cb3d9cd6
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0756
Une méthode partielle ne peut pas avoir plusieurs déclarations de définition.  
  
 La déclaration de définition d’une méthode partielle est la partie qui spécifie la signature de méthode, mais pas l’implémentation \(corps de méthode\). Une méthode partielle doit avoir exactement une déclaration de définition pour chaque signature unique. Chaque version surchargée d’une méthode partielle doit avoir sa propre déclaration de définition.  
  
### Pour corriger cette erreur  
  
1.  Supprimez toutes les déclarations de définition, sauf une, pour la méthode partielle.  
  
## Exemple  
  
```  
// cs0756.cs using System; public partial class C { partial void Part(); partial void Part(); // CS0756 public static int Main() { return 1; } }  
```  
  
## Voir aussi  
 [Classes et méthodes partielles](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)