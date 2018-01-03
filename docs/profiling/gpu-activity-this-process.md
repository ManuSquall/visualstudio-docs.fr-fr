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
ms.workload: multiple
ms.openlocfilehash: 2b395d47e6b338559b6f0bb22c8aef88ba183cd1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="gpu-activity-this-process"></a>Activité GPU (ce processus)
Les segments **Activité GPU (ce processus)** de la vue Threads du visualiseur concurrentiel représentent les périodes auxquelles le GPU a traité des demandes pour le compte du processus en cours. Ces demandes sont envoyées au GPU sous forme de paquets d’accès direct à la mémoire (DMA). La longueur d’un segment représente la durée pendant laquelle le GPU a traité un paquet DMA pour le compte du processus en cours.  
  
 Lorsque vous sélectionnez un segment d’activité GPU, le rapport sous l’onglet **Actuel** affiche des informations sur le paquet DMA qui a été traité. Ces informations incluent la durée pendant laquelle le paquet a attendu dans la file d’attente matérielle associée au moteur DirectX, le processus qui a envoyé le paquet, ainsi que le temps nécessaire pour traiter le paquet. Un processus autre que le processus en cours peut avoir envoyé physiquement le paquet DMA au GPU. Le visualiseur concurrentiel peut détecter si un autre processus envoie un travail au GPU pour le compte du processus en cours.