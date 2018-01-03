---
title: "Durée des E/S (vue Threads) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.timeline.io
helpviewer_keywords: Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: abea2c5ed246fe3463205894326a7f9611b56043
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="io-time-threads-view"></a>Durée des E/S (vue Threads)
Ces segments de la chronologie sont associés aux durées de blocage classées dans la catégorie des E/S. Cela signifie qu’un thread attend qu’une opération d’E/S se termine. Le thread peut avoir été bloqué dans une API ou par une attente du noyau liée à des E/S que le visualiseur concurrentiel traite comme E/S. Les API comme `CreateFile()`, `ReadFile()` et `WSARecv()` appartiennent à ce groupe.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Threads](../profiling/threads-view-parallel-performance.md)