---
title: "Erreur du compilateur CS1601 | Microsoft Docs"
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
  - "CS1601"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1601"
ms.assetid: 5efa1d2d-c70c-446d-a51f-d23d8a3be22e
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1601
Le paramètre de la méthode ou du délégué ne peut pas être de type 'type'  
  
 Certains types de la bibliothèque de classes .NET Framework, par exemple <xref:System.TypedReference>, <xref:System.RuntimeArgumentHandle> et <xref:System.ArgIterator>, ne peuvent pas être utilisés comme paramètres [ref](/dotnet/csharp/language-reference/keywords/ref) ou [out](/dotnet/csharp/language-reference/keywords/out), car ils peuvent potentiellement être utilisés pour des opérations non sécurisées.  
  
 L’exemple suivant génère l’erreur CS1601 :  
  
```  
// CS1601.cs using System; class MyClass { public void Test1 (ref TypedReference t)   // CS1601 { } public void Test2 (out ArgIterator t)   // CS1601 { } }  
```