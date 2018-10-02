---
title: Durée de préemption | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 614b049bf7aa881ce4454d8f832190b0391ff342
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507574"
---
# <a name="preemption-time"></a>Durée de préemption
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [durée de préemption](https://docs.microsoft.com/visualstudio/profiling/preemption-time).  
  
Ces segments de la chronologie sont associés au temps de blocage catégorisé comme Préemption. Cette catégorie implique qu’un thread est ignoré pour l’une des raisons suivantes :  
  
-   Le planificateur l’a remplacé par un thread de priorité plus élevée.  
  
-   Le quantum d’exécution du thread a expiré et d’autres threads étaient prêts à être exécutés.  
  
 Pendant cette période, un thread a été bloqué pour un motif lié à l’attente du noyau que le Visualiseur concurrentiel considère comme une préemption. Les segments de préemption commencent quand un thread est extrait d’un cœur logique, et se terminent quand l’exécution de ce thread reprend.  
  
 L’info-bulle d’un segment anticipé affiche le nom du processus ou du thread qui a provoqué la préemption. Toutefois, cela ne signifie pas que le processus ou le thread qui a pris le relais ait réellement été exécuté durant la période de préemption.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Threads](../profiling/threads-view-parallel-performance.md)



