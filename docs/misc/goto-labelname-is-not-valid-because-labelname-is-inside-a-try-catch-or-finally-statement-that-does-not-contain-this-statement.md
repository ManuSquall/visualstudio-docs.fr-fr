---
title: "&#39;GoTo &lt;nom_&#233;tiquette&gt;&#39; n’est pas valide, car &#39;&lt;nom_&#233;tiquette&gt;&#39; se trouve &#224; l’int&#233;rieur d’une instruction &#39;Try&#39;, &#39;Catch&#39; ou &#39;Finally&#39; qui ne contient pas cette instruction | Microsoft Docs"
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
  - "bc30754"
  - "vbc30754"
helpviewer_keywords: 
  - "BC30754"
ms.assetid: 2eefc7fb-fdf0-41e9-bf60-c3bc93580e14
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;GoTo &lt;nom_&#233;tiquette&gt;&#39; n’est pas valide, car &#39;&lt;nom_&#233;tiquette&gt;&#39; se trouve &#224; l’int&#233;rieur d’une instruction &#39;Try&#39;, &#39;Catch&#39; ou &#39;Finally&#39; qui ne contient pas cette instruction
Vous ne pouvez pas créer de branche dans un bloc `Try...Catch...Finally`.  
  
 **ID d’erreur :** BC30754  
  
### Pour corriger cette erreur  
  
-   Restructurez votre code pour que l’étiquette précède le bloc `Try...Catch...Finally`.  
  
## Voir aussi  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)