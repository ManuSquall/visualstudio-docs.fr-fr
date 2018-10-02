---
title: Durée de veille | Microsoft Docs
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
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd4d12097a8bf952cc0af0fa99025b9747ee7b3f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507378"
---
# <a name="sleep-time"></a>Durée de veille
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [durée de veille](https://docs.microsoft.com/visualstudio/profiling/sleep-time).  
  
Ces segments de la chronologie sont associés au temps de blocage catégorisé comme Veille. La catégorie Veille implique qu’un thread a volontairement abandonné son cœur logique et n’effectue aucun travail. Pendant cette période, un thread a été bloqué dans une API que le visualiseur concurrentiel considère comme étant de la veille. Les API comme `Sleep()` et `SwitchToThread()` appartiennent à ce groupe.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Threads](../profiling/threads-view-parallel-performance.md)



