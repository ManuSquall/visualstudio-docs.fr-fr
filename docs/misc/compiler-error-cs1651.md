---
title: "Erreur du compilateur&#160;CS1651 | Microsoft Docs"
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
  - "CS1651"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1651"
ms.assetid: ce1043e3-b453-4b4c-b949-f344834e3845
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur&#160;CS1651
Les champs d’un champ readonly statique 'identifier' ne peuvent pas être passés en ref ou out \(sauf s’ils appartiennent à un constructeur statique\)  
  
 Cette erreur se produit si vous passez une variable en tant qu’argument ref à une fonction membre d’un champ readonly statique. Étant donné que les paramètres ref peuvent être modifiés par la fonction, cela n’est pas autorisé. Pour résoudre cette erreur, supprimez le mot clé **readonly** du champ ou ne passez pas les membres du champ readonly à la fonction. Par exemple, vous pouvez essayer de créer une variable temporaire modifiable et de la passer en tant qu’argument ref, comme illustré dans l’exemple suivant.  
  
 L’exemple suivant génère l’erreur CS1651 :  
  
```  
// CS1651.cs public struct Inner { public int i; } class Outer { public static readonly Inner inner = new Inner(); } class D { static void f(ref int iref) { } static void Main() { f(ref Outer.inner.i);  // CS1651 // Try this instead: // int tmp = Outer.inner.i; // f(ref tmp); } }  
```