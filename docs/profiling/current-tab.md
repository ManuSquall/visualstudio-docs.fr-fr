---
title: Onglet Actuel | Microsoft Docs
description: Sélectionnez l’onglet actuel de la vue threads pour afficher une pile d’appels pour un segment de thread de l’UC ou un segment de blocage. Il contient également des informations sur les segments DirectX.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.reportnav.current
helpviewer_keywords:
- Concurrency Visualizer, Callstack at Selection Point
ms.assetid: 2c7b1ae5-3756-4795-bc59-f6bb113f2ba5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4125a40ea0be18cceb99e7f3a8118a10d26a5437
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955864"
---
# <a name="current-tab"></a>Onglet actuel
En cliquant sur l’onglet **Actuel**, vous pouvez voir la pile des appels (si disponible) qui est la plus proche du point de sélection actuel dans la chronologie si un segment de thread de processeur est sélectionné.  Dans ce cas, le point de sélection est représenté par une flèche noire, ou point d’insertion, au-dessus de la chronologie. Lorsqu’un segment de blocage est sélectionné, le point d’insertion n’est pas affiché, car il n’y a pas d’exécution. Toutefois, le segment est encore sélectionné et une pile des appels est affichée.

 L’onglet **Actuel** affiche également des informations sur les segments d’activité DirectX, les marqueurs et les accès d’E/S.  Pour les segments d’activité DirectX, des informations sur la façon dont les paquets DMA sont traités par la file d’attente matérielle sont affichées.  Pour les marqueurs, une description et des informations de type sont affichées.  Pour les accès d’E/S, des informations sur le fichier et le nombre d’octets lus ou écrits sont affichées.

## <a name="see-also"></a>Voir aussi
- [vue Threads](../profiling/threads-view-parallel-performance.md)