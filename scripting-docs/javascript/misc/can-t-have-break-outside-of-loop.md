---
title: "Impossible d&#39;utiliser une instruction &#39;break&#39; en dehors d&#39;une boucle | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1019"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Impossible d&#39;utiliser une instruction &#39;break&#39; en dehors d&#39;une boucle
Vous avez tenté d'utiliser le mot clé **break** en dehors d'une boucle.  Le mot clé **break** est utilisé pour terminer une boucle ou une instruction `switch`.  Il doit être incorporé dans le corps d'une boucle ou d'une instruction `switch`.  Toutefois, une **étiquette** peut suivre le mot clé break.  
  
```  
break labelname;  
```  
  
 Vous avez uniquement besoin de la forme étiquetée du mot clé **break** lorsque vous utilisez des boucles imbriquées ou des instructions `switch` et que vous devez quitter une boucle qui n'est pas la plus profonde.  
  
### Pour corriger cette erreur  
  
-   Assurez\-vous que le mot clé **break** apparaît dans une boucle englobante ou une instruction switch.  
  
## Voir aussi  
 [break, instruction](../../javascript/reference/break-statement-javascript.md)   
 [Contrôle du flux de programme](../../javascript/controlling-program-flow-javascript.md)   
 [Dépannage de vos scripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)