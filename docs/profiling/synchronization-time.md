---
title: Période de synchronisation | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f3236530c1a7b92fd1cba1bdd61e3e1c0973b58c
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35668693"
---
# <a name="synchronization-time"></a>Période de synchronisation
Ces segments de la chronologie sont associés à des périodes de blocage classées dans la catégorie Synchronisation. Quand un thread est marqué comme bloqué sur la synchronisation, cela implique une de ces situations :  
  
-   L’exécution du thread peut avoir abouti à un appel à une API de synchronisation de threads connue, comme `EnterCriticalSection()` ou `WaitForSingleObject()`.  
  
-   L’algorithme correspondant de l’API ne peut pas être entièrement exhaustif et par conséquent, certaines API qui peuvent être mappées à d’autres catégories peuvent également apparaître comme étant une synchronisation, car une trame dans la pile des appels a finalement atteint une primitive de blocage du noyau sous-jacent qui a été mappée à cette catégorie.  
  
 Pour comprendre la cause sous-jacente d’un événement de blocage de thread, examinez attentivement les piles des appels bloquants et les rapports de profil.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Threads](../profiling/threads-view-parallel-performance.md)