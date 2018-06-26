---
title: Durée d’exécution (vue Threads) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1b06532771aaa432deccb8040c7dd7e5962dd15f
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764428"
---
# <a name="execution-time-threads-view"></a>Durée d’exécution (vue Threads)
Ces segments de la chronologie de la vue Threads représentent la durée d’exécution, lorsque le thread effectue un travail sur un cœur logique du système.  
  
 Les changements d’état du thread sont détectés via les événements de changement de contexte du noyau. Le suivi d’événements pour Windows (ETW) capture des échantillons de piles chaque milliseconde. Dans un segment vert très court, il est possible qu’aucun échantillon ne soit capturé. Par conséquent, certains segments d’exécution courts peuvent ne pas afficher de pile d’appels.  
  
 Lorsque vous cliquez sur un segment d’exécution, le visualiseur concurrentiel affiche l’échantillon de pile le plus proche de l’emplacement du clic. L’emplacement de cet échantillon de pile est indiqué par une flèche noire (ou signe insertion) au-dessus de la chronologie. L’échantillon de pile apparaît également sous l’onglet **Actuel**.  
  
 Pour afficher un profil d’échantillonnage classique pour tous les segments d’exécution de la vue actuelle, cliquez sur **Exécution** dans le profil de la chronologie visible.  
  
## <a name="see-also"></a>Voir aussi  
 [Profil d’exécution, rapport](../profiling/execution-profile-report.md)   
 [Vue Threads](../profiling/threads-view-parallel-performance.md)