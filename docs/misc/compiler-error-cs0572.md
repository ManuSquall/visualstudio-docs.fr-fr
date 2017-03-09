---
title: "Erreur du compilateur CS0572 | Microsoft Docs"
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
  - "CS0572"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0572"
ms.assetid: ec950e95-13da-41b5-90cd-9e673d62498b
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0572
'type' : impossible de référencer un type par l’intermédiaire d’une expression ; essayez plutôt 'path\_to\_type'  
  
 Une tentative a été effectuée pour accéder à un membre d’une classe via un identificateur, ce qui n’est pas autorisé dans cette situation.  
  
 L’exemple suivant génère l’erreur CS0572 :  
  
```  
// CS0572.cs using System; class C { public class Inner { public static int v = 9; } } class D : C { public static void Main() { C cValue = new C(); Console.WriteLine(cValue.Inner.v);   // CS0572 // try the following line instead // Console.WriteLine(C.Inner.v); } }  
```