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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3d988ab3e381ef8c5d25eed1978eed39c53e9e24
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49272140"
---
# <a name="gpu-activity-other-processes"></a>Activité GPU (autres processus)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les segments **Activité GPU (autres processus)** de la vue Threads du visualiseur concurrentiel représentent les périodes auxquelles le GPU a traité des demandes pour le compte d’autres processus du système. Ces demandes sont envoyées au GPU sous forme de paquets d’accès direct à la mémoire (DMA).  La longueur d’un segment représente la durée pendant laquelle le paquet a été traité par le GPU.  
  
 Lorsque vous sélectionnez ce type de segment, le rapport sous l’onglet **Actuel** affiche des informations sur le paquet qui a été traité.  Ces informations incluent la durée pendant laquelle le paquet a attendu dans la file d’attente matérielle associée au moteur DirectX, le processus qui a envoyé le paquet, ainsi que le temps nécessaire pour traiter le paquet.



