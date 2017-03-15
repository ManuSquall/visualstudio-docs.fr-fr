---
title: "Erreur du compilateur CS1528 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1528"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1528"
ms.assetid: 38aabc5c-b32f-4bea-a585-c4212f42751d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1528
; ou \= attendu \(impossible de spécifier des arguments de constructeur dans une déclaration\)  
  
 Une référence à une classe a été spécifiée comme si un objet de la classe était créé. Par exemple, une tentative de passer une variable à un constructeur a eu lieu. Utilisez l’opérateur [new](/dotnet/csharp/language-reference/keywords/new) pour créer un objet d’une classe.  
  
 L’exemple suivant génère l’erreur CS1528 :  
  
```  
// CS1528.cs using System; public class B { public B(int i) { _i = i; } public void PrintB() { Console.WriteLine(_i); } private int _i; } public class mine { public static void Main() { B b(3);   // CS1528, reference is not an object // try one of the following // B b; // or // B bb = new B(3); // bb.PrintB(); } }  
```