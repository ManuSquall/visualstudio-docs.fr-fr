---
title: "Avertissement du compilateur (niveau&#160;4) CS0402 | Microsoft Docs"
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
  - "CS0402"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0402"
ms.assetid: 5a252c95-18c7-4569-bae0-e1f7b582cf6a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;4) CS0402
'identifier' : un point d’entrée ne peut pas être générique ni dans un type générique  
  
 Le point d’entrée a été trouvé dans un type générique. Pour supprimer cet avertissement, implémentez Main dans une classe ou une structure non générique.  
  
```  
// CS0402.cs // compile with: /W:4 class C<T> { public static void Main()  // CS0402 { } } class CMain { public static void Main() {} }  
```