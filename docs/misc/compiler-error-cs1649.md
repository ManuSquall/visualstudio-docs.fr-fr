---
title: "Erreur du compilateur CS1649 | Microsoft Docs"
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
  - "CS1649"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1649"
ms.assetid: 6355c7f2-157c-441d-8925-500062988636
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1649
Les membres d’un champ readonly 'identifier' ne peuvent pas être passés en ref ou out \(sauf s’ils appartiennent à un constructeur\)  
  
 Cette erreur se produit si vous passez une variable en tant qu’argument `ref` ou `out` à une fonction membre d’un champ `readonly`. Étant donné que les paramètres `ref` et `out` peuvent être modifiés par la fonction, cette opération n’est pas autorisée. Pour résoudre cette erreur, supprimez le mot clé `readonly` du champ ou ne passez pas les membres du champ `readonly` à la fonction. Par exemple, vous pouvez essayer de créer une variable temporaire modifiable et de la passer en tant qu’argument `ref`, comme illustré dans l’exemple suivant.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1649 :  
  
```  
// CS1649.cs public struct Inner { public int i; } class Outer { public readonly Inner inner = new Inner(); } class D { static void f(ref int iref) { } static void Main() { Outer outer = new Outer(); f(ref outer.inner.i);  // CS1649 // Try this code instead: // int tmp = outer.inner.i; // f(ref tmp); } }  
```