---
title: "Erreur du compilateur CS0407 | Microsoft Docs"
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
  - "CS0407"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0407"
ms.assetid: 59112fb9-4641-466e-b738-b3228539a09e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0407
'return\-type method' ne possède pas le type de retour correct  
  
 La méthode n’est pas compatible avec le type délégué. Les types d’argument correspondent, mais le type de retour n’est pas le type de retour correct pour ce délégué. Pour éviter cette erreur, utilisez une méthode différente, modifiez le type de retour de la méthode ou celui du délégué.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0407 :  
  
```  
// CS0407.cs public delegate int MyDelegate(); class C { MyDelegate d; public C() { d = new MyDelegate(F);  // OK: F returns int d = new MyDelegate(G);  // CS0407 – G doesn't return int } public int F() { return 1; } public void G() { } public static void Main() { C c1 = new C(); } }  
```