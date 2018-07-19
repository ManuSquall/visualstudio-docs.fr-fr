---
title: Onglet actuel | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.reportnav.current
helpviewer_keywords:
- Concurrency Visualizer, Callstack at Selection Point
ms.assetid: 2c7b1ae5-3756-4795-bc59-f6bb113f2ba5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9964da1521852d942490c09b83135c62f6be3ed9
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749497"
---
# <a name="current-tab"></a>Onglet actuel
En cliquant sur l’onglet **Actuel**, vous pouvez voir la pile des appels (si disponible) qui est la plus proche du point de sélection actuel dans la chronologie si un segment de thread de processeur est sélectionné.  Dans ce cas, le point de sélection est représenté par une flèche noire, ou point d’insertion, au-dessus de la chronologie. Lorsqu’un segment de blocage est sélectionné, le point d’insertion n’est pas affiché, car il n’y a pas d’exécution. Toutefois, le segment est encore sélectionné et une pile des appels est affichée.  
  
 L’onglet **Actuel** affiche également des informations sur les segments d’activité DirectX, les marqueurs et les accès d’E/S.  Pour les segments d’activité DirectX, des informations sur la façon dont les paquets DMA sont traités par la file d’attente matérielle sont affichées.  Pour les marqueurs, une description et des informations de type sont affichées.  Pour les accès d’E/S, des informations sur le fichier et le nombre d’octets lus ou écrits sont affichées.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Threads](../profiling/threads-view-parallel-performance.md)