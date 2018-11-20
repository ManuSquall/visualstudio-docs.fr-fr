---
title: Activité GPU (pagination) | Microsoft Docs
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
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cba0335a7090bc8f7308d5a64e8fedebedd99a6e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789926"
---
# <a name="gpu-activity-paging"></a>Activité GPU (pagination)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les segments **Activité GPU (pagination)** sous l’onglet Threads représentent les périodes auxquelles le GPU a traité les requêtes de pagination.  La longueur d’un segment représente la durée pendant laquelle le GPU a traité un paquet de pagination d’accès direct à la mémoire (DMA). En règle générale, les paquets de pagination sont associés au transfert de mémoire entre le processeur et le GPU.  
  
 Lorsque vous sélectionnez un segment de pagination GPU, le rapport sous l’onglet **Actuel** affiche des informations sur le paquet DMA qui a été traité. Ces informations incluent la durée pendant laquelle le paquet a attendu dans la file d’attente matérielle associée au moteur DirectX, le processus qui a envoyé le paquet DMA, ainsi que le temps nécessaire pour traiter le paquet.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Utilisation](../profiling/utilization-view.md)



