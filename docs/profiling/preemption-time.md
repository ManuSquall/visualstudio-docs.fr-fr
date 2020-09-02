---
title: Durée de préemption | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de7a02f7247e09876bc4598d44fc1c395161ebc2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62935891"
---
# <a name="preemption-time"></a>Durée de préemption
Ces segments de la chronologie sont associés au temps de blocage catégorisé comme Préemption. Cette catégorie implique qu’un thread est ignoré pour l’une des raisons suivantes :

- Le planificateur l’a remplacé par un thread de priorité plus élevée.

- Le quantum d’exécution du thread a expiré et d’autres threads étaient prêts à être exécutés.

  Pendant cette période, un thread a été bloqué pour un motif lié à l’attente du noyau que le Visualiseur concurrentiel considère comme une préemption. Les segments de préemption commencent quand un thread est extrait d’un cœur logique, et se terminent quand l’exécution de ce thread reprend.

  L’info-bulle d’un segment anticipé affiche le nom du processus ou du thread qui a provoqué la préemption. Toutefois, cela ne signifie pas que le processus ou le thread qui a pris le relais ait réellement été exécuté durant la période de préemption.

## <a name="see-also"></a>Voir aussi
- [vue Threads](../profiling/threads-view-parallel-performance.md)