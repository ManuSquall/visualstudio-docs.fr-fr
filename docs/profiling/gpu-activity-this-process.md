---
title: "Activité GPU (ce processus) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 255a1ff62d4f9c444169e1330dcd11eb8e1030ed
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="gpu-activity-this-process"></a>Activité GPU (ce processus)
Les segments **Activité GPU (ce processus)** de la vue Threads du visualiseur concurrentiel représentent les périodes auxquelles le GPU a traité des demandes pour le compte du processus en cours. Ces demandes sont envoyées au GPU sous forme de paquets d’accès direct à la mémoire (DMA). La longueur d’un segment représente la durée pendant laquelle le GPU a traité un paquet DMA pour le compte du processus en cours.  
  
 Lorsque vous sélectionnez un segment d’activité GPU, le rapport sous l’onglet **Actuel** affiche des informations sur le paquet DMA qui a été traité. Ces informations incluent la durée pendant laquelle le paquet a attendu dans la file d’attente matérielle associée au moteur DirectX, le processus qui a envoyé le paquet, ainsi que le temps nécessaire pour traiter le paquet. Un processus autre que le processus en cours peut avoir envoyé physiquement le paquet DMA au GPU. Le visualiseur concurrentiel peut détecter si un autre processus envoie un travail au GPU pour le compte du processus en cours.