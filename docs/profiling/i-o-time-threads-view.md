---
title: Durée des E/S (vue Threads) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d7ba29383ddddc02160967a90b56046128d2f19
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62995444"
---
# <a name="io-time-threads-view"></a>temps consacré aux E/S (vue Threads)
Ces segments de la chronologie sont associés aux durées de blocage classées dans la catégorie des E/S. Cela signifie qu’un thread attend qu’une opération d’E/S se termine. Le thread peut avoir été bloqué dans une API ou par une attente du noyau liée à des E/S que le visualiseur concurrentiel traite comme E/S. Les API comme `CreateFile()`, `ReadFile()` et `WSARecv()` appartiennent à ce groupe.

## <a name="see-also"></a>Voir aussi
- [Vue Threads](../profiling/threads-view-parallel-performance.md)