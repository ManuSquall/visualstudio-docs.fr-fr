---
title: Période de synchronisation | Microsoft Docs
description: Découvrez comment les segments de la chronologie sont associés aux temps de blocage catégorisés comme synchronisation.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0e8c2243d01a5801b6846445995bbdfdcff78c9
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719823"
---
# <a name="synchronization-time"></a>Période de synchronisation
Ces segments de la chronologie sont associés à des périodes de blocage classées dans la catégorie Synchronisation. Quand un thread est marqué comme bloqué sur la synchronisation, cela implique une de ces situations :

- L’exécution du thread peut avoir abouti à un appel à une API de synchronisation de threads connue, comme `EnterCriticalSection()` ou `WaitForSingleObject()`.

- L’algorithme correspondant de l’API ne peut pas être entièrement exhaustif et par conséquent, certaines API qui peuvent être mappées à d’autres catégories peuvent également apparaître comme étant une synchronisation, car une trame dans la pile des appels a finalement atteint une primitive de blocage du noyau sous-jacent qui a été mappée à cette catégorie.

  Pour comprendre la cause sous-jacente d’un événement de blocage de thread, examinez attentivement les piles des appels bloquants et les rapports de profil.

## <a name="see-also"></a>Voir aussi
- [Vue threads](../profiling/threads-view-parallel-performance.md)