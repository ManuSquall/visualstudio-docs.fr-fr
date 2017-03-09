---
title: "Erreur du compilateur CS1626 | Microsoft Docs"
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
  - "CS1626"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1626"
ms.assetid: 3ba03383-eb24-4fd8-bf40-8b0f7d6baf0d
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1626
Impossible de générer une valeur dans le corps d'un bloc try avec une clause catch  
  
 L’instruction yield n’est pas autorisée dans un bloc try si une clause catch est associée au bloc try. Pour éviter cette erreur, placez l’instruction yield en dehors de la clause catch.  
  
 L’exemple suivant génère l’erreur CS1626 :  
  
```  
// CS1626.cs using System.Collections; class C : IEnumerable { public IEnumerator GetEnumerator() { try { yield return this;  // CS1626 } catch { } } } public class CMain { public static void Main() { } }  
  
```