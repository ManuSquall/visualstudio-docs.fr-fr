---
title: Activité GPU (ce processus) | Microsoft Docs
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
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1b0949a71dc4db1ee217d691d4aae7928faf301
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751406"
---
# <a name="gpu-activity-this-process"></a>Activité GPU (ce processus)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les segments **Activité GPU (ce processus)** de la vue Threads du visualiseur concurrentiel représentent les périodes auxquelles le GPU a traité des demandes pour le compte du processus en cours. Ces demandes sont envoyées au GPU sous forme de paquets d’accès direct à la mémoire (DMA). La longueur d’un segment représente la durée pendant laquelle le GPU a traité un paquet DMA pour le compte du processus en cours.  
  
 Lorsque vous sélectionnez un segment d’activité GPU, le rapport sous l’onglet **Actuel** affiche des informations sur le paquet DMA qui a été traité. Ces informations incluent la durée pendant laquelle le paquet a attendu dans la file d’attente matérielle associée au moteur DirectX, le processus qui a envoyé le paquet, ainsi que le temps nécessaire pour traiter le paquet. Un processus autre que le processus en cours peut avoir envoyé physiquement le paquet DMA au GPU. Le visualiseur concurrentiel peut détecter si un autre processus envoie un travail au GPU pour le compte du processus en cours.



