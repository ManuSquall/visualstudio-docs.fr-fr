---
title: "Segment de chronologie vide | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.empty"
helpviewer_keywords: 
  - "Visualiseur concurrentiel, segment de chronologie vide"
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Segment de chronologie vide
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans le visualiseur concurrentiel, la raison pour laquelle une section de la chronologie est vide \(a un arrière\-plan blanc\) dépend du type du canal.  
  
-   Pour un canal de thread de l'UC, cela signifie que le thread n'existait pas pendant cette partie de la chronologie.  Si vous êtes interessé par le thread, vous pouvez rechercher sa section d'exécution en utilisant le contrôle de zoom ou en faisant défiler horizontalement.  
  
-   Pour un canal d'E\/S, cela signifie qu'aucun accès au disque s'est produit pour le compte du processus cible à ce moment.  
  
-   Pour un canal DirectX, cela signifie qu'aucun travail de GPU n'a été effectué au nom du processus cible pendant cette partie de la chronologie.  
  
-   Pour un canal de jeton, cela signifie qu'aucun jeton n'a été générée.  
  
## Voir aussi  
 [vue Threads](../profiling/threads-view-parallel-performance.md)   
 [Contrôle Zoom \(vue Threads\)](../profiling/zoom-control-threads-view.md)