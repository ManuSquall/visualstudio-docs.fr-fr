---
title: "Erreur du compilateur CS1650 | Microsoft Docs"
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
  - "CS1650"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1650"
ms.assetid: 251a3a67-6e56-4795-874a-d54610c70595
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1650
Impossible d’assigner les champs du champ readonly statique 'identifier' \(sauf s’ils appartiennent à un constructeur statique ou un initialiseur de variable\)  
  
 Cette erreur se produit quand vous tentez de modifier un membre d’un champ readonly et static qui n’autorise pas les modifications. Pour résoudre cette erreur, limitez les assignations aux champs readonly au constructeur ou à l’initialiseur de variable, ou supprimez le mot clé `readonly` de la déclaration du champ.  
  
```  
// CS1650.cs public struct Inner { public int i; } class Outer { public static readonly Inner inner = new Inner(); } class D { static void Main() { Outer.inner.i = 1;  // CS1650 } }  
```