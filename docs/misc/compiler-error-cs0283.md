---
title: "Erreur du compilateur CS0283 | Microsoft Docs"
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
  - "CS0283"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0283"
ms.assetid: f94a5b84-92c5-4602-894d-6f856d57e0e6
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0283
Le type 'type' ne peut pas être déclaré const  
  
 Le type spécifié dans une déclaration de constante doit être `byte`, `char`, `short`, `int`, `long`, `float`, `double`, `decimal`, `bool`, `string`, un type enum ou un type référence auquel est affecté la valeur null. Chaque expression de constante doit produire une valeur du type cible ou d’un type qui peut être converti vers le type cible par une conversion implicite.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0283.  
  
```  
// CS0283.cs struct MyTest { } class MyClass { // To resolve the error but retain the "const-ness", // change const to readonly. const MyTest test = new MyTest();   // CS0283 public static int Main() { return 1; } }  
```