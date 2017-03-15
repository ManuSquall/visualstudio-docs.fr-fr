---
title: "Erreur du compilateur CS1513 | Microsoft Docs"
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
  - "CS1513"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1513"
ms.assetid: 28dacbb5-bf60-49ac-878e-c0ce469114eb
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1513
} attendue  
  
 Le compilateur attendait une accolade fermante \(`}`\) qui n’a pas été trouvée.  
  
 L’exemple suivant génère l’erreur CS1513 :  
  
```  
// CS1513 namespace y   // CS1513, no close curly brace { class x { public static void Main() { } }  
```