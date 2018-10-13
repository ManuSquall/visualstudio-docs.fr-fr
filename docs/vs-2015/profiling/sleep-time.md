---
title: Durée de veille | Microsoft Docs
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
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 92e19fff86d61c033ab49ea77de6fd395f00beb0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245257"
---
# <a name="sleep-time"></a>Durée de veille
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ces segments de la chronologie sont associés au temps de blocage catégorisé comme Veille. La catégorie Veille implique qu’un thread a volontairement abandonné son cœur logique et n’effectue aucun travail. Pendant cette période, un thread a été bloqué dans une API que le visualiseur concurrentiel considère comme étant de la veille. Les API comme `Sleep()` et `SwitchToThread()` appartiennent à ce groupe.  
  
## <a name="see-also"></a>Voir aussi  
 [vue Threads](../profiling/threads-view-parallel-performance.md)



