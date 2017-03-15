---
title: "Erreur du compilateur CS0687 | Microsoft Docs"
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
  - "CS0687"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0687"
ms.assetid: b51c5e7c-f4de-4aa4-97b1-ebe220cd19b0
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0687
Le qualificateur d’alias d’espace de noms '::' est toujours résolu en type ou en espace de noms ; il est donc non conforme ici. Utilisez '.' à la place.  
  
 Cette erreur se produit si vous avez utilisé un élément que l’analyseur a interprété comme un type dans un emplacement inattendu. Un nom de type ou d’espace de noms est valide uniquement dans une expression d’accès au membre, à l’aide de l’opérateur d’accès au membre \(**.**\). Cela peut se produire si vous avez utilisé l’opérateur de portée globale \(::\) dans un autre contexte.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0687 :  
  
```  
// CS0687.cs using M = Test; using System; public class Test { public static int x = 77; public static void Main() { Console.WriteLine(M::x); // CS0687 // To resolve use the following line instead: // Console.WriteLine(M.x); } }  
```