---
title: "Activité GPU (autres processus) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bd39910631ce67693e1e039307813a5ded13e326
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="gpu-activity-other-processes"></a>Activité GPU (autres processus)
Les segments **Activité GPU (autres processus)** de la vue Threads du visualiseur concurrentiel représentent les périodes auxquelles le GPU a traité des demandes pour le compte d’autres processus du système. Ces demandes sont envoyées au GPU sous forme de paquets d’accès direct à la mémoire (DMA).  La longueur d’un segment représente la durée pendant laquelle le paquet a été traité par le GPU.  
  
 Lorsque vous sélectionnez ce type de segment, le rapport sous l’onglet **Actuel** affiche des informations sur le paquet qui a été traité.  Ces informations incluent la durée pendant laquelle le paquet a attendu dans la file d’attente matérielle associée au moteur DirectX, le processus qui a envoyé le paquet, ainsi que le temps nécessaire pour traiter le paquet.