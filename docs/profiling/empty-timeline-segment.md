---
title: Segment de chronologie vide | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a3411de6fbc4d30f3b8dcb3dbe7a8eeba12e8ad9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959367"
---
# <a name="empty-timeline-segment"></a>Segment de chronologie vide
Dans le visualiseur concurrentiel, la raison d’un segment de chronologie vide (avec un arrière-plan blanc) dépend du type de canal.  
  
-   Pour un canal de thread d’UC, cela signifie que le thread n’existait pas à cette période. Pour en savoir plus sur le thread, regardez sa section d’exécution en utilisant le contrôle de zoom ou en faisant défiler la page horizontalement.  
  
-   Pour un canal d’E/S, cela signifie qu’aucun accès disque ne s’est produit pour le compte du processus cible à ce moment précis.  
  
-   Pour un canal DirectX, cela signifie qu’aucun travail GPU n’a été effectué pour le compte du processus cible pendant cette période.  
  
-   Pour un canal de marqueur, cela signifie qu’aucun marqueur n’a été généré.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Threads](../profiling/threads-view-parallel-performance.md)   
 [Contrôle Zoom (vue Threads)](../profiling/zoom-control-threads-view.md)