---
title: Activité GPU (autres processus) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c7d68547e0c2d0b056e2c60f1e9e183270841c6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55030260"
---
# <a name="gpu-activity-other-processes"></a>Activité GPU (autres processus)
Les segments **Activité GPU (autres processus)** de la vue Threads du visualiseur concurrentiel représentent les périodes auxquelles le GPU a traité des demandes pour le compte d’autres processus du système. Ces demandes sont envoyées au GPU sous forme de paquets d’accès direct à la mémoire (DMA).  La longueur d’un segment représente la durée pendant laquelle le paquet a été traité par le GPU.  
  
 Lorsque vous sélectionnez ce type de segment, le rapport sous l’onglet **Actuel** affiche des informations sur le paquet qui a été traité.  Ces informations incluent la durée pendant laquelle le paquet a attendu dans la file d’attente matérielle associée au moteur DirectX, le processus qui a envoyé le paquet, ainsi que le temps nécessaire pour traiter le paquet.