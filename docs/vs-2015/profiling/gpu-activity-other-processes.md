---
title: Activité GPU (autres processus) | Microsoft Docs
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
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a5b38423bd629dee0f518e0f62eedcf7c55c1db0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789835"
---
# <a name="gpu-activity-other-processes"></a>Activité GPU (autres processus)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les segments **Activité GPU (autres processus)** de la vue Threads du visualiseur concurrentiel représentent les périodes auxquelles le GPU a traité des demandes pour le compte d’autres processus du système. Ces demandes sont envoyées au GPU sous forme de paquets d’accès direct à la mémoire (DMA).  La longueur d’un segment représente la durée pendant laquelle le paquet a été traité par le GPU.  
  
 Lorsque vous sélectionnez ce type de segment, le rapport sous l’onglet **Actuel** affiche des informations sur le paquet qui a été traité.  Ces informations incluent la durée pendant laquelle le paquet a attendu dans la file d’attente matérielle associée au moteur DirectX, le processus qui a envoyé le paquet, ainsi que le temps nécessaire pour traiter le paquet.



