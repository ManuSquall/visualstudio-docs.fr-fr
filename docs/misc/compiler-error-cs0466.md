---
title: "Erreur du compilateur CS0466 | Microsoft Docs"
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
  - "CS0466"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0466"
ms.assetid: db6be72b-120a-4b48-b41c-a738d02adae0
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0466
'méthode1' ne doit pas avoir de paramètre params, car 'méthode2' n’en possède pas  
  
 Vous ne pouvez pas utiliser le paramètre `params` sur un membre de classe si l’interface implémentée ne l’utilise pas.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0466 :  
  
```  
// CS0466.cs interface I { void F1(params int[] a); void F2(int[] a); } class C : I { void I.F1(params int[] a) {} void I.F2(params int[] a) {}   // CS0466 void I.F2(int[] a) {}   // OK public static void Main() { I i = (I) new C(); i.F1(new int[] {1, 2} ); i.F2(new int[] {1, 2} ); } }  
```