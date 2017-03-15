---
title: "&#39;End Select&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;Select Case&#39; correspondant | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30088"
  - "vbc30088"
helpviewer_keywords: 
  - "BC30088"
ms.assetid: 9de8c0d4-4ce9-45cf-98d6-8f68bba507a5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Select&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;Select Case&#39; correspondant
Une instruction `End Select` ne possède pas d’instruction `Select` ou `Select Case` correspondante.`End Select` doit être précédé d’une instruction `Select` ou `Select Case`.  
  
 **ID d’erreur :** BC30088  
  
### Pour corriger cette erreur  
  
1.  Si ce bloc `Select` fait partie d’un ensemble de blocs `Select` imbriqués, vérifiez que chaque bloc est correctement terminé.  
  
2.  Vérifiez que les autres structures de contrôle du bloc `Select` ont été correctement terminées.  
  
3.  Vérifiez que ce bloc `Select` est correctement formaté.  
  
## Voir aussi  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)