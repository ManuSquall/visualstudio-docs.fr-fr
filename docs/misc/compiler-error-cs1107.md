---
title: "Erreur du compilateur CS1107 | Microsoft Docs"
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
  - "CS1107"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1107"
ms.assetid: 1b6f6790-53af-4261-a14f-bf2db9790f0b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1107
Un paramètre ne peut posséder qu’un modificateur 'modifier name'.  
  
 Si les modificateurs de paramètre comme `this`, `ref` et `out` apparaissent plusieurs fois dans une définition de paramètre, cela provoque une erreur.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1107 :  
  
```  
// cs1107.cs public static class Test { // Extension methods. public static void TestMethod(this this t) {} // CS1107 // Regular Instance Method public void TestMethod(ref ref int i) {} // CS1107 }  
```