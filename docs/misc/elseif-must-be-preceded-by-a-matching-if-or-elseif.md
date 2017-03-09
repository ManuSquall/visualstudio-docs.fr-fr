---
title: "&#39;ElseIf&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;If&#39; ou &#39;ElseIf&#39; correspondant | Microsoft Docs"
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
  - "bc36005"
  - "vbc36005"
helpviewer_keywords: 
  - "BC36005"
ms.assetid: bcebae85-b438-4839-bada-2f8f8dcc8a86
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ElseIf&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;If&#39; ou &#39;ElseIf&#39; correspondant
Une instruction `ElseIf` se produit sans instruction `If` correspondante.`ElseIf` doit être précédé d’une instruction `If` ou d’une autre instruction `ElseIf`.  
  
 **ID d’erreur :** BC36005  
  
### Pour corriger cette erreur  
  
1.  Si ce bloc `If` fait partie d’un ensemble de structures de contrôle imbriquées, vérifiez que chaque structure est correctement terminée.  
  
2.  Vérifiez que les autres structures de contrôle imbriquées dans ce bloc `If` sont correctement terminées.  
  
3.  Vérifiez que ce bloc `If` a été correctement mis en forme.  
  
## Voir aussi  
 [If...Then...Else Statement](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)   
 [Decision Structures](/dotnet/visual-basic/programming-guide/language-features/control-flow/decision-structures)