---
title: Durée de veille | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b94b1695eb36aa8f55847c21a14d72357d51a405
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35668896"
---
# <a name="sleep-time"></a>Durée de veille
Ces segments de la chronologie sont associés au temps de blocage catégorisé comme Veille. La catégorie Veille implique qu’un thread a volontairement abandonné son cœur logique et n’effectue aucun travail. Pendant cette période, un thread a été bloqué dans une API que le visualiseur concurrentiel considère comme étant de la veille. Les API comme `Sleep()` et `SwitchToThread()` appartiennent à ce groupe.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Threads](../profiling/threads-view-parallel-performance.md)