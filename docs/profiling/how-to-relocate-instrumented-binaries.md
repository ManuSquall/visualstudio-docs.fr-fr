---
title: "Comment&#160;: d&#233;placer des binaires instrument&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.binaries"
helpviewer_keywords: 
  - "binaires, instrumentés"
  - "instrumentation, binaires instrumentés"
  - "binaires instrumentés et déplacement"
  - "outils de profilage, binaires instrumentés"
ms.assetid: 258f49e8-4b09-477e-a132-8fad685b66f4
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Comment&#160;: d&#233;placer des binaires instrument&#233;s
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lors de l’instrumentation, des sondes sont insérées dans le fichier binaire pour mesurer les performances de l’application. Quand vous choisissez de déplacer le fichier binaire instrumenté, une copie du fichier binaire d’origine est instrumentée et placée à l’emplacement spécifié. Cette option est utile si vous ne voulez pas que le profileur renomme votre fichier binaire d’origine. Si le fichier binaire n’est pas déplacé, la version d’origine du fichier binaire est remplacée.  
  
 **Spécifications**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### Pour déplacer un fichier binaire instrumenté  
  
1.  Dans l’**Explorateur de performances**, cliquez avec le bouton droit sur la session de performance, puis cliquez sur **Propriétés**.  
  
2.  Dans les **Pages de propriétés**, cliquez sur les propriétés **Binaire**.  
  
3.  Cochez la case **Déplacer les fichiers binaires instrumentés**.  
  
4.  Spécifiez l’emplacement du fichier binaire instrumenté.  
  
## Voir aussi  
 [Configuration de sessions de performance](../profiling/configuring-performance-sessions.md)   
 [VSInstr](../profiling/vsinstr.md)