---
title: "Activit&#233; GPU (ce processus) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.gpuexecution"
  - "vs.cv.threads.timeline.gpuactivity"
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Activit&#233; GPU (ce processus)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les segments **activité du GPU \(ce processus\)** dans la vue Threads dans le visualiseur d'accès concurrentiel représentent des périodes pendant lesquelles le GPU traitait des demandes pour le compte du processus actuel.  Ces requêtes sont envoyées au GPU comme paquets d'accès direct à la mémoire \(DMA\).  La longueur d'un segment représente le temps que le GPU mettait à traiter un paquet d'accès direct à la mémoire pour le compte du processus actuel.  
  
 Lorsque vous sélectionnez le segment d'activité du GPU, le rapport sous l'onglet **Actuel** affiche des informations sur le paquet DMA qui a été traité.  Les informations comprennent la durée que le paquet a dû attendre dans la file d'attente du matériel qui est associée au moteur DirectX, le processus qui a envoyé le paquet, et le temps qui a été requis pour traiter le paquet.  Un processus autre que le processus actuel a peut\-être physiquement soumis le paquet d'accès direct à la mémoire au GPU.  Le visualiseur d'accès concurrentiel peut détecter lorsqu'un autre processus a envoyé un travail au GPU pour le compte du processus courant.