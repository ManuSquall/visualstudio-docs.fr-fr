---
title: "&#39;Else&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;If&#39; ou &#39;ElseIf&#39; correspondant | Microsoft Docs"
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
  - "bc30086"
  - "vbc30086"
helpviewer_keywords: 
  - "BC30086"
ms.assetid: 5e76b3c6-571f-4a6f-b524-26150cb6e986
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Else&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;If&#39; ou &#39;ElseIf&#39; correspondant
Une instruction `Else` apparaît sans une instruction `If` correspondante.`Else` doit être précédé d’une instruction `If`.  
  
 **ID d’erreur :** BC30086  
  
### Pour corriger cette erreur  
  
1.  Si ce bloc `If` fait partie d’un ensemble de blocs `If` imbriqués, vérifiez que chaque bloc se termine correctement.  
  
2.  Vérifiez que les autres structures de contrôle du bloc `If` sont correctement terminées.  
  
3.  Vérifiez que ce bloc `If` est mis en forme correctement.  
  
## Voir aussi  
 [If...Then...Else Statement](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)