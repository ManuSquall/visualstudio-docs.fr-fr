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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: edb4cf928426fb39adbbfdc18382b7d5de6c6b4e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54963682"
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