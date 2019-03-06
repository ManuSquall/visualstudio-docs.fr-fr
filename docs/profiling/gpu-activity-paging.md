---
title: Activité GPU (pagination) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8bd28c7b41a01992ad52fa343b098b0a02460806
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608329"
---
# <a name="gpu-activity-paging"></a>Activité GPU (pagination)
Les segments **Activité GPU (pagination)** sous l’onglet **Threads** représentent les périodes auxquelles le GPU a traité les requêtes de pagination.  La longueur d’un segment représente la durée pendant laquelle le GPU a traité un paquet de pagination d’accès direct à la mémoire (DMA). En règle générale, les paquets de pagination sont associés au transfert de mémoire entre le processeur et le GPU.

 Lorsque vous sélectionnez un segment de pagination GPU, le rapport sous l’onglet **Actuel** affiche des informations sur le paquet DMA qui a été traité. Ces informations incluent la durée pendant laquelle le paquet a attendu dans la file d’attente matérielle associée au moteur DirectX, le processus qui a envoyé le paquet DMA, ainsi que le temps nécessaire pour traiter le paquet.

## <a name="see-also"></a>Voir aussi
- [Vue Utilisation](../profiling/utilization-view.md)