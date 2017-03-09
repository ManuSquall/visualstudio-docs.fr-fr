---
title: "Erreur du compilateur CS0248 | Microsoft Docs"
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
  - "CS0248"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0248"
ms.assetid: a7ddfd26-a836-47b8-b432-53876e06da31
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0248
Impossible de créer un tableau avec une taille négative  
  
 Une taille de tableau a été spécifiée avec un nombre négatif. Pour plus d'informations, consultez [Tableaux](/dotnet/csharp/programming-guide/arrays/index).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0248 :  
  
```  
// CS0248.cs class MyClass { public static void Main() { int[] myArray = new int[-3] {1,2,3};   // CS0248, pass a nonnegative number } }  
```