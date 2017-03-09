---
title: "Erreur du compilateur CS1686 | Microsoft Docs"
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
  - "CS1686"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1686"
ms.assetid: 46a9e82b-57f4-416d-8e49-242bfff5433a
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1686
L’adresse de la variable locale 'variable' ou de ses membres ne peut pas être prise et utilisée dans une méthode anonyme ou une expression lambda  
  
 Cette erreur est générée lorsque vous utilisez une variable, que vous tentez de prendre son adresse et que l’une de ces actions s’effectue à l’intérieur d’une méthode anonyme.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1686.  
  
```  
// CS1686.cs // compile with: /unsafe /target:library class MyClass { public unsafe delegate int * MyDelegate(); public unsafe int * Test() { int j = 0; MyDelegate d = delegate { return &j; };   // CS1686 return &j;   // OK } }  
```