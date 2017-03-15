---
title: "Dur&#233;e de veille | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.sleep"
helpviewer_keywords: 
  - "Visualiseur concurrence, Durée de veille"
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Dur&#233;e de veille
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ces segments de la chronologie sont associés au temps de blocage catégorisé comme Veille.  La catégorie de veille implique qu'un thread a volontairement abandonné son cœur logique et n'accomplit aucun travail.  Pendant ce temps, un thread a été bloqué dans une API que le visualiseur d'accès concurrentiel considère comme veille.  Les API telles que `Sleep()` et `SwitchToThread()` appartiennent à ce groupe.  
  
## Voir aussi  
 [vue Threads](../profiling/threads-view-parallel-performance.md)