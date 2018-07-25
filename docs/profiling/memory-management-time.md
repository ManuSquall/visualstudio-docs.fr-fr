---
title: Période de gestion de la mémoire | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0284d312a4157c41f93fec17d601406c669a83c1
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35238249"
---
# <a name="memory-management-time"></a>Période de gestion de la mémoire
Ces segments de la chronologie sont associés aux temps de blocage classés dans la catégorie de gestion de la mémoire. Ce scénario implique qu’un thread est bloqué par un événement associé à une opération de gestion de la mémoire telle que la pagination. Pendant cette période, un thread a été bloqué dans un état d’API ou de noyau que le visualiseur concurrentiel considère comme de la gestion de la mémoire. Cela inclut la pagination et l’allocation de mémoire.  
  
 Examinez les piles d’appels et les rapports de profils associés pour mieux comprendre les raisons sous-jacentes des blocages classés dans la catégorie Gestion de mémoire.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Threads](../profiling/threads-view-parallel-performance.md)