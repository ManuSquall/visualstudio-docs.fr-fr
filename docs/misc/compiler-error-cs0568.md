---
title: "Erreur du compilateur CS0568 | Microsoft Docs"
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
  - "CS0568"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0568"
ms.assetid: dc9e1263-f58d-4c95-9165-27ba7757bc7b
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0568
Les structures ne peuvent pas contenir de constructeurs exempts de paramètres explicites  
  
 Chaque [struct](/dotnet/csharp/language-reference/keywords/struct) a déjà un constructeur par défaut qui initialise l’objet à zéro. Les constructeurs que vous pouvez créer pour un struct doivent donc accepter un ou plusieurs paramètres.  
  
 L’exemple suivant génère l’erreur CS0568 :  
  
```  
// CS0568.cs public struct ClassY { public int field1; public ClassY(){}   // CS0568, cannot have no param constructor // Try following instead: // public ClassY(int i) // { //    field1 = i; // } } public class ClassX { public static void Main() { } }  
```