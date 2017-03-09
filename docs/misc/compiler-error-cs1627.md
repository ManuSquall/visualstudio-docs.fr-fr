---
title: "Erreur du compilateur&#160;CS1627 | Microsoft Docs"
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
  - "CS1627"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1627"
ms.assetid: 58dd6e22-e9ed-4e5c-ae04-ce255f07064e
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur&#160;CS1627
Expression attendue après yield return  
  
 Cette erreur se produit si `yield` est utilisé sans expression. Pour éviter cette erreur, insérez l’expression appropriée dans l’instruction.  
  
 L’exemple suivant génère l’erreur CS1627 :  
  
```  
// CS1627.cs using System.Collections; class C : IEnumerable { public IEnumerator GetEnumerator() { yield return;   // CS1627 // To resolve, add the following line: // yield return 0; } } public class CMain { public static void Main() { } }  
```