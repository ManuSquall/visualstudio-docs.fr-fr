---
title: "Erreur du compilateur CS1631 | Microsoft Docs"
ms.custom: ""
ms.date: "10/01/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1631"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1631"
ms.assetid: bf0c5ff9-90a3-4db6-b4ee-0b93e31614e0
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1631
Impossible de générer une valeur dans le corps d'une clause catch  
  
 L’instruction yield n’est pas autorisée à partir du corps d’une clause catch. Pour éviter cette erreur, placez l’instruction yield en dehors du corps de la clause catch.  
  
 L’exemple suivant génère l’erreur CS1631 :  
  
```  
// CS1631.cs using System; using System.Collections; public class C : IEnumerable { public IEnumerator GetEnumerator() { try { } catch(Exception e) { yield return this;  // CS1631 } } public static void Main() { } }  
```