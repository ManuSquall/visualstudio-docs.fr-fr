---
title: Segment de chronologie vide | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4ac39a776cb7e6c2c9cbce648c0b3ca3ebc86783
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54770743"
---
# <a name="empty-timeline-segment"></a>Segment de chronologie vide
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans le visualiseur concurrentiel, la raison d’un segment de chronologie vide (avec un arrière-plan blanc) dépend du type de canal.  
  
-   Pour un canal de thread d’UC, cela signifie que le thread n’existait pas à cette période. Pour en savoir plus sur le thread, regardez sa section d’exécution en utilisant le contrôle de zoom ou en faisant défiler la page horizontalement.  
  
-   Pour un canal d’E/S, cela signifie qu’aucun accès disque ne s’est produit pour le compte du processus cible à ce moment précis.  
  
-   Pour un canal DirectX, cela signifie qu’aucun travail GPU n’a été effectué pour le compte du processus cible pendant cette période.  
  
-   Pour un canal de marqueur, cela signifie qu’aucun marqueur n’a été généré.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Threads](../profiling/threads-view-parallel-performance.md)   
 [Contrôle Zoom (vue Threads)](../profiling/zoom-control-threads-view.md)
