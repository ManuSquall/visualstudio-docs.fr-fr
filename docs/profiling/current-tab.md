---
title: "Onglet actif | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.reportnav.current"
helpviewer_keywords: 
  - "visualiseur concurrentiel, pile des appels au niveau du point de sélection"
ms.assetid: 2c7b1ae5-3756-4795-bc59-f6bb113f2ba5
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Onglet actif
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En cliquant sur l'onglet **Actuel**, vous pouvez consulter la pile des appels \(si disponible\) qui est la plus proche du point de sélection actuel dans la chronologie si un segment de thread CPU est sélectionné.  Dans ce cas, le point de sélection est représenté par une flèche noire ou signe insertion, au\-dessus de la chronologie.  Lorsqu'un segment bloquant est sélectionné, le signe insertion n'est pas affiché parce que aucune exécution n'était en cours.  Toutefois, le segment demeure en surbrillance et une pile des appels est affichée.  
  
 L'onglet **Actuel** affiche également des informations sur les segments d'activité de DirectX, les marqueurs, et les accès E\/S.  Pour les segments d'activité de DirectX, les informations sur la façon dont les paquets d'accès direct à la mémoire sont traités par la file d'attente matérielle sont affichées.  Pour les marqueurs, les informations sur la description et le type de marqueur s'affichent.  Pour les accès E\/S, les informations sur le fichier et le nombre d'octets lus ou écrits sont affichées.  
  
## Voir aussi  
 [vue Threads](../profiling/threads-view-parallel-performance.md)