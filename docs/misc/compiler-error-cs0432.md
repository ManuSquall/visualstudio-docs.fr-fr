---
title: "Erreur du compilateur CS0432 | Microsoft Docs"
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
  - "CS0432"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0432"
ms.assetid: 39b63146-ecb2-4b7a-b3cb-f68fff5069f6
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0432
Alias 'identificateur' introuvable  
  
 Cette erreur se produit quand vous placez « :: » à droite d’un identificateur qui n’est pas un alias. Pour résoudre cette erreur, utilisez « . » à la place de « :: ».  
  
 L’exemple suivant génère l’erreur CS0432 :  
  
```  
// CS0432.cs namespace A { public class B { public static void Meth() { } } } public class Test { public static void Main() { A::B.Meth();   // CS0432 // To resolve, use the following line instead: // A.B.Meth(); } }  
```