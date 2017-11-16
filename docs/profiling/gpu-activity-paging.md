---
title: "Activité GPU (pagination) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 960ea3a50a5c937b93b81c56e3b775d3fde49bd8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="gpu-activity-paging"></a>Activité GPU (pagination)
Les segments **Activité GPU (pagination)** sous l’onglet Threads représentent les périodes auxquelles le GPU a traité les requêtes de pagination.  La longueur d’un segment représente la durée pendant laquelle le GPU a traité un paquet de pagination d’accès direct à la mémoire (DMA). En règle générale, les paquets de pagination sont associés au transfert de mémoire entre le processeur et le GPU.  
  
 Lorsque vous sélectionnez un segment de pagination GPU, le rapport sous l’onglet **Actuel** affiche des informations sur le paquet DMA qui a été traité. Ces informations incluent la durée pendant laquelle le paquet a attendu dans la file d’attente matérielle associée au moteur DirectX, le processus qui a envoyé le paquet DMA, ainsi que le temps nécessaire pour traiter le paquet.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Utilisation](../profiling/utilization-view.md)