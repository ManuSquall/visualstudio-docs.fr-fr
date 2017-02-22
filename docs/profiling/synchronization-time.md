---
title: "Dur&#233;e de synchronisation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.synchronization"
helpviewer_keywords: 
  - "Visualiseur concurrence, Durée de synchronisation"
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Dur&#233;e de synchronisation
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ces segments de la chronologie sont associés aux temps de blocage catégorisés comme synchronisation.  Lorsqu'un thread est marqué comme bloqué en synchronisation, l'une de causes suivantes en est à l'origine :  
  
-   L'exécution du thread a pu provoquer un appel d'une API de synchronisation de threads connue telle que `EnterCriticalSection()` ou `WaitForSingleObject()`.  
  
-   L'algorithme de mappage des API ne peut pas être complet, par conséquent, certaines API qui auraient pu être mappées à d'autres catégories peuvent également être catégorisées comme synchronisation car une frame de la pile des appels a réussi à atteindre une primitive de blocage de noyau sous\-jacente déjà mappée à cette catégorie.  
  
 Pour comprendre la cause sous\-jacente d'un événement de blocage de thread, examinez attentivement les piles d'appels bloquantes et les rapports de profil.  
  
## Voir aussi  
 [vue Threads](../profiling/threads-view-parallel-performance.md)