---
title: "Avertissement du compilateur (niveau&#160;1) CS1633 | Microsoft Docs"
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
  - "CS1633"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1633"
ms.assetid: f31db218-f880-4fc4-ab34-8bcdc49011da
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS1633
Directive \#pragma non reconnue  
  
 Le pragma utilisé n’est pas l’un des pragmas connus pris en charge par le compilateur C\#. Pour résoudre cette erreur, utilisez uniquement des pragmas pris en charge.  
  
 L’exemple suivant génère l’avertissement CS1633 :  
  
```  
// CS1633.cs // compile with: /W:1 #pragma unknown  // CS1633 class C { public static void Main() { } }  
```