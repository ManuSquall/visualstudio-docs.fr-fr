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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf64339f25e392d4e5790673d77d078b84d02c7c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826609"
---
# <a name="io-time-threads-view"></a>temps consacré aux E/S (vue Threads)
Ces segments de la chronologie sont associés aux durées de blocage classées dans la catégorie des E/S. Cela signifie qu’un thread attend qu’une opération d’E/S se termine. Le thread peut avoir été bloqué dans une API ou par une attente du noyau liée à des E/S que le visualiseur concurrentiel traite comme E/S. Les API comme `CreateFile()`, `ReadFile()` et `WSARecv()` appartiennent à ce groupe.  
  
## <a name="see-also"></a>Voir aussi  
 [vue Threads](../profiling/threads-view-parallel-performance.md)