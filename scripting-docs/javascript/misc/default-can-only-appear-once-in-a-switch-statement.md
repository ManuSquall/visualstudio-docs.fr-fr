---
title: "&#39;default&#39; ne peut appara&#238;tre qu&#39;une fois dans une instruction &#39;switch&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT1027"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# &#39;default&#39; ne peut appara&#238;tre qu&#39;une fois dans une instruction &#39;switch&#39;
Vous avez tenté d'utiliser l'instruction **default** à plusieurs reprises dans une instruction switch.  L'instruction default case est toujours la dernière instruction case utilisée dans une instruction switch \(c'est la case laissée pour compte\).  
  
### Pour corriger cette erreur  
  
-   Supprimez les instructions **default** case en trop de votre instruction `switch` \(utilisez une instruction case par défaut maximum par instruction switch\).  
  
## Voir aussi  
 [switch, instruction](../../javascript/reference/switch-statement-javascript.md)   
 [Contrôle du flux de programme](../../javascript/controlling-program-flow-javascript.md)   
 [Mots réservés JavaScript](../../javascript/reference/javascript-reserved-words.md)