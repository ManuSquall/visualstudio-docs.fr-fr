---
title: "Erreur du compilateur CS0111 | Microsoft Docs"
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
  - "CS0111"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0111"
ms.assetid: 87afb689-f27b-451d-84eb-d6bdf17aea41
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0111
Le type 'class' définit déjà un membre appelé 'member' avec les mêmes types de paramètres  
  
 L’erreur CS0111 se produit si une classe contient deux déclarations membres avec le même nom et les mêmes types de paramètres. Pour plus d'informations, consultez [Méthodes](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0111.  
  
```  
// CS0111.cs class A { void Test() { } public static void Test(){}   // CS0111 public static void Main() {} }  
```