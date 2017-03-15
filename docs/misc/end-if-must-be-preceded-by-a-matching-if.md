---
title: "&#39;End If&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;If&#39; correspondant. | Microsoft Docs"
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
  - "bc30087"
  - "vbc30087"
helpviewer_keywords: 
  - "BC30087"
ms.assetid: 81c056bb-267e-44ef-9a44-3a41273090ea
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End If&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;If&#39; correspondant.
Une instruction `End If` apparaît sans une instruction `If` correspondante.`End If` doit être précédé d’une instruction `If`.  
  
 **ID d’erreur :** BC30087  
  
### Pour corriger cette erreur  
  
1.  Si ce bloc `If` fait partie d’un ensemble de blocs `If` imbriqués, vérifiez que chaque bloc se termine correctement.  
  
2.  Vérifiez que les autres structures de contrôle du bloc `If` sont correctement terminées.  
  
3.  Vérifiez que ce bloc `If` est correctement formaté.  
  
## Voir aussi  
 [If...Then...Else Statement](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)