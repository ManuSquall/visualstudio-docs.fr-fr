---
title: "&#39;End With&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;With&#39; correspondant | Microsoft Docs"
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
  - "bc30093"
  - "vbc30093"
helpviewer_keywords: 
  - "BC30093"
ms.assetid: b0f1f7d5-0c33-4b97-8043-f0f5b40ca5d7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End With&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;With&#39; correspondant
Une instruction `End With` se produit sans instruction `With` correspondante.`End With` doit être précédé d’une instruction `With` correspondante.  
  
 **ID d’erreur :** BC30093  
  
### Pour corriger cette erreur  
  
1.  Si ce bloc `With` fait partie d’un ensemble de blocs `With` imbriqués, vérifiez que chaque bloc se termine correctement.  
  
2.  Vérifiez que les autres structures de contrôle du bloc `With` sont correctement terminées.  
  
3.  Vérifiez que ce bloc `With` est mis en forme correctement.  
  
## Voir aussi  
 [With...End With Statement](/dotnet/visual-basic/language-reference/statements/with-end-with-statement)