---
title: "R&#232;gles de performance de m&#233;moire et de pagination | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# R&#232;gles de performance de m&#233;moire et de pagination
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les règles de performance de la catégorie Mémoire et pagination identifient l'activité de pagination dans une exécution du profilage qui peut affecter les performances et la réactivité de l'application.  
  
|||  
|-|-|  
|[DA0014 : Taux élevés de pagination de la mémoire active sur le disque](../Topic/DA0014:%20Extremely%20high%20rates%20of%20paging%20active%20memory%20to%20disk.md)|Un taux extrêmement élevé de mémoire active de pagination vers le disque et à partir du disque a été relevé dans toute l'exécution du profilage.  Les taux de pagination à ce niveau ont généralement un impact sur les performances et la réactivité de l'application.  Envisagez de réduire les allocations de mémoire en modifiant les algorithmes.  Il vous faudra peut\-être également prendre en compte les besoins en mémoire de votre application.  Essayez d'exécuter à nouveau le profilage sur un ordinateur disposant de davantage de mémoire.  Cette règle se déclenche lorsque la quantité d'activité de pagination dépasse le seuil supérieur de la règle D0017.|  
|[DA0017 : taux élevés de pagination de la mémoire active sur le disque](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Un taux relativement élevé de mémoire active de pagination vers le disque et à partir du disque a été relevé dans toute l'exécution du profilage.  Les taux de pagination à ce niveau ont généralement un impact sur les performances et la réactivité de l'application.  Envisagez de réduire les allocations de mémoire en modifiant les algorithmes.  Il vous faudra peut\-être également prendre en compte les besoins en mémoire de votre application.  Essayez d'exécuter à nouveau le profilage sur un ordinateur disposant de davantage de mémoire.|