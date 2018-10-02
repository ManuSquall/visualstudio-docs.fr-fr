---
title: Période de gestion de la mémoire | Microsoft Docs
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
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9371c4d5249539c80299fd1b1573eba19c9dd14f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493384"
---
# <a name="memory-management-time"></a>Période de gestion de la mémoire
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [temps de gestion de mémoire](https://docs.microsoft.com/visualstudio/profiling/memory-management-time).  
  
Ces segments de la chronologie sont associés aux temps de blocage classés dans la catégorie de gestion de la mémoire. Cela implique qu’un thread est bloqué par un événement associé à une opération de gestion de la mémoire telle que la pagination. Pendant cette période, un thread a été bloqué dans un état d’API ou de noyau que le visualiseur concurrentiel considère comme de la gestion de la mémoire. Cela inclut la pagination et l’allocation de mémoire.  
  
 Examinez les piles d’appels et les rapports de profils associés pour mieux comprendre les raisons sous-jacentes des blocages classés dans la catégorie Gestion de mémoire.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Threads](../profiling/threads-view-parallel-performance.md)



