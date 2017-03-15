---
title: "&#39;GoTo &lt;nom_&#233;tiquette&gt;&#39; n’est pas valide, car &#39;&lt;nom_&#233;tiquette&gt;&#39; se trouve &#224; l’int&#233;rieur d’une instruction &#39;SyncLock&#39; qui ne contient pas cette instruction | Microsoft Docs"
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
  - "bc30755"
  - "vbc30755"
helpviewer_keywords: 
  - "BC30755"
ms.assetid: 95fb48c1-4982-45fc-81f0-f30cf0df173f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;GoTo &lt;nom_&#233;tiquette&gt;&#39; n’est pas valide, car &#39;&lt;nom_&#233;tiquette&gt;&#39; se trouve &#224; l’int&#233;rieur d’une instruction &#39;SyncLock&#39; qui ne contient pas cette instruction
Vous ne pouvez pas créer de branche dans un bloc `SyncLock`.  
  
 **ID d’erreur :** BC30755  
  
### Pour corriger cette erreur  
  
-   Restructurez votre code pour que l’étiquette précède le bloc `SyncLock`.  
  
## Voir aussi  
 [SyncLock Statement](/dotnet/visual-basic/language-reference/statements/synclock-statement)