---
title: "P&#233;riode de gestion de la m&#233;moire | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.paging"
helpviewer_keywords: 
  - "visualiseur concurrentiel, durée de pagination"
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# P&#233;riode de gestion de la m&#233;moire
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ces segments de la chronologie sont associés aux temps de blocage catégorisés comme gestion de la mémoire.  Cela implique qu'un thread est bloqué par un événement associé à une opération de gestion de la mémoire telle que la pagination.  Durant cette période, un thread a été bloqué dans une API ou par l'état du noyau que le visualiseur concurrentiel traite comme gestion de la mémoire.  Les événements concernés sont la pagination et l'allocation de mémoire.  
  
 Examinez les piles d'appels et les rapports de profil associés pour mieux comprendre les causes à l'origine de la catégorisation des blocs comme Gestion de la mémoire.  
  
## Voir aussi  
 [vue Threads](../profiling/threads-view-parallel-performance.md)