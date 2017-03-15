---
title: "Activit&#233; GPU (autres processus) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.gpuother"
  - "vs.cv.threads.timeline.gpuactivity"
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Activit&#233; GPU (autres processus)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les segments **activité de GPU \(autre processus\)** dans la vue Threads du Visualiseur concurrentiel représentent des périodes pendant lesquelles le GPU traitait des demandes de la part d'autres processus sur le système.  Ces requêtes sont envoyées au GPU comme paquets d'accès direct à la mémoire \(DMA\).  La longueur d'un segment représente la durée pendant laquelle l'en\-tête pack a été traitée par le GPU.  
  
 Lorsque vous sélectionnez ce genre de segment, le rapport sous l'onglet **Actuel** affiche des informations sur le paquet qui a été traité.  Les informations comprennent la durée que le paquet a dû attendre dans la file d'attente du matériel qui est associé au moteur de DirectX, le processus qui a envoyé le paquet, et le temps qui a été requis pour traiter le paquet.