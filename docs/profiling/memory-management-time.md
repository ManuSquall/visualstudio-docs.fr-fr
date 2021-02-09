---
title: Période de gestion de la mémoire | Microsoft Docs
description: Découvrez comment ce scénario implique qu’un thread est bloqué par un événement qui est associé à une opération de gestion de la mémoire telle que la pagination.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ad3c913e6c983749e53940f5e75ad3bdba48bf92
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873630"
---
# <a name="memory-management-time"></a>Période de gestion de la mémoire
Ces segments de la chronologie sont associés aux temps de blocage classés dans la catégorie de gestion de la mémoire. Ce scénario implique qu’un thread est bloqué par un événement associé à une opération de gestion de la mémoire telle que la pagination. Pendant cette période, un thread a été bloqué dans un état d’API ou de noyau que le visualiseur concurrentiel considère comme de la gestion de la mémoire. Cela inclut la pagination et l’allocation de mémoire.

 Examinez les piles d’appels et les rapports de profils associés pour mieux comprendre les raisons sous-jacentes des blocages classés dans la catégorie Gestion de mémoire.

## <a name="see-also"></a>Voir aussi
- [vue Threads](../profiling/threads-view-parallel-performance.md)