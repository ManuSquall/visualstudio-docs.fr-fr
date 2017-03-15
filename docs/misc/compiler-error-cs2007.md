---
title: "Erreur du compilateur CS2007 | Microsoft Docs"
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
  - "CS2007"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2007"
ms.assetid: 9be20e8e-2424-4435-9371-778fb12823c0
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS2007
Option de ligne de commande non reconnue : 'option'  
  
 Une chaîne a été passée au compilateur, mais il ne s’agissait pas d’une [option du compilateur](/dotnet/csharp/language-reference/compiler-options/index), même si elle commençait par une barre oblique \(\/\).  
  
 L’exemple suivant génère l’erreur CS2007 :  
  
```  
// CS2007.cs // compile with: /recur // CS2007 expected class x { public static void Main() {} }  
```