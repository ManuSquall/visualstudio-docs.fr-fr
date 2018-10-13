---
title: Durée des E/S (vue Threads) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55050ad6ed805c2996cfc52561b17e2614a6ee12
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236793"
---
# <a name="io-time-threads-view"></a>Durée des E/S (vue Threads)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ces segments de la chronologie sont associés aux durées de blocage classées dans la catégorie des E/S. Cela signifie qu’un thread attend qu’une opération d’E/S se termine. Le thread peut avoir été bloqué dans une API ou par une attente du noyau liée à des E/S que le visualiseur concurrentiel traite comme E/S. Les API comme `CreateFile()`, `ReadFile()` et `WSARecv()` appartiennent à ce groupe.  
  
## <a name="see-also"></a>Voir aussi  
 [vue Threads](../profiling/threads-view-parallel-performance.md)



