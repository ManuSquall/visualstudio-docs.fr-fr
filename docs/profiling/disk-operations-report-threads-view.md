---
title: "Rapport sur les op&#233;rations sur le disque (Vue Threads) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.report.diskoperations"
helpviewer_keywords: 
  - "Visualiseur concurrentiel, rapport des opérations sur les fichiers (vue Threads)"
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Rapport sur les op&#233;rations sur le disque (Vue Threads)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les compte rendu des opérations de disque affiche des opérations d'E\/S de disque dans les canaux de disque.  
  
 Pour chaque accès au disque qui se passe au nom du processus profilé dans la fenêtre de temps actuellement visible, ces informations sont stockées :  
  
-   Le nom et l'ID Processus \(PID\) du processus qui a exécuté l'accès au disque  
  
-   ID du thread qui a accédé au disque.  
  
-   Nom du fichier qui a été accédé.  
  
-   Le nombre de lectures par fichier  
  
-   Nombre d'octets lus  
  
-   La latence de lecture, en millisecondes  
  
-   Le nombre d'écritures  
  
-   Le nombre d'octets écrits  
  
-   La latence d'écriture, en millisecondes  
  
## Voir aussi  
 [vue Threads](../profiling/threads-view-parallel-performance.md)