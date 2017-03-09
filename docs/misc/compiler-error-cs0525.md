---
title: "Erreur du compilateur CS0525 | Microsoft Docs"
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
  - "CS0525"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0525"
ms.assetid: fcecfd4f-221f-41e6-a95c-1685be78926e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0525
Les interfaces ne peuvent pas contenir de champs  
  
 Une [interface](/dotnet/csharp/language-reference/keywords/interface) peut contenir des méthodes et des propriétés, mais pas des champs.  
  
 L’exemple suivant génère l’erreur CS0525 :  
  
```  
// CS0525.cs namespace x { public interface clx { public int i;   // CS0525 } }  
```