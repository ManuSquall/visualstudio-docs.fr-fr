---
title: "Erreur du compilateur CS0564 | Microsoft Docs"
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
  - "CS0564"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0564"
ms.assetid: 4c152e10-eb22-4437-a85f-1599c76470e0
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0564
Le premier opérande d'un opérateur de décalage surchargé doit être du même type que le type conteneur et le type du second opérande doit être int  
  
 Vous avez tenté de surcharger un opérateur de décalage \(\<\< ou \>\>\) avec des opérandes de type incorrect. Le premier opérande doit être le type et le second opérande doit être de type `int`.  
  
 L’exemple suivant génère l’erreur CS0564 :  
  
```  
// CS0564.cs using System; class C { public static int operator << (C c1, C c2) // CS0564 // To correct, change second operand to int, like so: // public static int operator << (C c1, int c2) { return 0; } static void Main() { } }  
```