---
title: "Erreur du compilateur CS1648 | Microsoft Docs"
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
  - "CS1648"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1648"
ms.assetid: 5cf1bc84-cd18-4df2-942f-1cc17eabacd6
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1648
Les membres d’un champ readonly 'identifier' ne peuvent pas être modifiés \(sauf s’ils appartiennent à un constructeur ou un initialiseur de variable\)  
  
 Cette erreur se produit quand vous tentez de modifier un membre de champ readonly qui ne peut pas être modifié. Pour résoudre cette erreur, limitez les assignations aux champs readonly au constructeur ou à l’initialiseur de variable, ou supprimez le mot clé readonly de la déclaration du champ.  
  
 L’exemple suivant génère l’erreur CS1648 :  
  
```  
// CS1648.cs public struct Inner { public int i; } class Outer { public readonly Inner inner = new Inner(); } class D { static void Main() { Outer outer = new Outer(); outer.inner.i = 1;  // CS1648 } }  
```