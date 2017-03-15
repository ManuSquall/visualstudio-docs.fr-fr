---
title: "&#39;With&#39; doit se terminer par un &#39;End With&#39; correspondant | Microsoft Docs"
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
  - "bc30085"
  - "vbc30085"
helpviewer_keywords: 
  - "BC30085"
ms.assetid: aa88f4d0-be5f-4efe-a4ef-80e6d6124e6e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;With&#39; doit se terminer par un &#39;End With&#39; correspondant
Il existe une occurrence d’instruction `With` sans instruction `End With` correspondante. Vous devez utiliser une instruction `End With` pour terminer le bloc `With`.  
  
 **ID d’erreur :** BC30085  
  
### Pour corriger cette erreur  
  
-   Si ce bloc `With` fait partie d’un ensemble de blocs `With` imbriqués, vérifiez que chaque bloc se termine correctement.  
  
-   Ajoutez une instruction `End With` à la fin du bloc `With`.  
  
## Voir aussi  
 [With...End With Statement](/dotnet/visual-basic/language-reference/statements/with-end-with-statement)