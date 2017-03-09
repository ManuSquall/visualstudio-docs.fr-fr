---
title: "&#39;End While&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;While&#39; correspondant | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30090"
  - "bc30090"
helpviewer_keywords: 
  - "BC30090"
ms.assetid: 302b26b8-8fa4-4e49-86f0-d7c49fec485f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End While&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;While&#39; correspondant
Une instruction `End While` se produit sans instruction `While` correspondante.`End While` doit être précédé d’une instruction `While` correspondante.  
  
 **ID d’erreur :** BC30090  
  
### Pour corriger cette erreur  
  
1.  Si ce bloc `While` fait partie d’un ensemble de blocs `While` imbriqués, vérifiez que chaque bloc est correctement terminé.  
  
2.  Vérifiez que les autres structures de contrôle du bloc `While` ont été correctement terminées.  
  
3.  Vérifiez que ce bloc `While` a été correctement mis en forme.  
  
## Voir aussi  
 [While...End While Statement](/dotnet/visual-basic/language-reference/statements/while-end-while-statement)