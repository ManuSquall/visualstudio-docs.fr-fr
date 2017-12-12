---
title: "Durée de veille | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.timeline.sleep
helpviewer_keywords: Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 52ce4aa37b607072a0cf91c4baf0dbe6b077ac5e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="sleep-time"></a>Durée de veille
Ces segments de la chronologie sont associés au temps de blocage catégorisé comme Veille. La catégorie Veille implique qu’un thread a volontairement abandonné son cœur logique et n’effectue aucun travail. Pendant cette période, un thread a été bloqué dans une API que le visualiseur concurrentiel considère comme étant de la veille. Les API comme `Sleep()` et `SwitchToThread()` sont rattachées à ce groupe.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Threads](../profiling/threads-view-parallel-performance.md)