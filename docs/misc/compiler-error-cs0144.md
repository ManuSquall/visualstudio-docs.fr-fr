---
title: "Erreur du compilateur CS0144 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0144"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0144"
ms.assetid: 3904cab1-05bd-44ec-81d0-e36c5656f742
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0144
Impossible de créer une instance de la classe abstraite ou de l’interface 'interface'  
  
 Vous ne pouvez pas créer une instance d’une classe [abstraite](/dotnet/csharp/language-reference/keywords/abstract) ou d’une [interface](/dotnet/csharp/language-reference/keywords/interface). Pour plus d'informations, consultez [Interfaces](/dotnet/csharp/programming-guide/interfaces/index).  
  
 L’exemple suivant génère l’erreur CS0144 :  
  
```  
// CS0144.cs interface MyInterface { } public class MyClass { public static void Main() { MyInterface myInterface = new MyInterface ();   // CS0144 } }  
```