---
title: "Erreur du compilateur CS1599 | Microsoft Docs"
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
  - "CS1599"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1599"
ms.assetid: 4cdb282d-0f5d-459b-afc1-8980fbb22067
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1599
Ni la méthode, ni le délégué ne peuvent retourner un type 'type'  
  
 Certains types de la bibliothèque de classes .NET Framework, par exemple, <xref:System.TypedReference>, <xref:System.RuntimeArgumentHandle> et <xref:System.ArgIterator>, ne peuvent pas être utilisés en tant que types de retour, car ils peuvent potentiellement être utilisés pour des opérations non sécurisées.  
  
 L’exemple suivant génère l’erreur CS1599 :  
  
```  
// CS1599.cs using System; class MyClass { public static void Main() { } public TypedReference Test1()   // CS1599 { return null; } public ArgIterator Test2()   // CS1599 { return null; } }  
```