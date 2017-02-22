---
title: "R&#232;gles de performance de l&#39;analyse de ressource | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# R&#232;gles de performance de l&#39;analyse de ressource
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les messages de performances de la catégorie Analyse de ressource fournissent des données supplémentaires sur les performances de votre application.  Vous pouvez utiliser ces données pour analyser les problèmes de performances.  Ces règles sont fournies à titre informatif et signalées pour chaque exécution du profilage.  
  
|||  
|-|-|  
|[DA0501 : consommation processeur moyenne par le processus en cours de profilage.](../Topic/DA0501:%20Average%20CPU%20consumption%20by%20the%20Process%20being%20profiled..md)|Ce message signale le pourcentage de temps pendant lequel un processeur était occupé à exécuter des instructions à partir de l'application.  La valeur signalée est la moyenne de tous les intervalles de mesure dans lesquels le processus profilé était actif.|  
|[DA0502 : consommation processeur maximale par le processus en cours de profilage](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|Ce message signale le pourcentage maximal de temps pendant lequel un processeur était occupé à exécuter des instructions à partir de l'application.  La valeur signalée est la valeur maximale de tous les intervalles de mesure dans lesquels le processus profilé était actif.|  
|[DA0503 : jeu de travail moyen, en octets, pour le processus en cours de profilage](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|Ce message signale la quantité moyenne de mémoire physique, en octets, que le processus utilisait lorsque le profilage était actif.  Cette mesure de mémoire physique est appelée « jeu de travail ».|  
|[DA0504 : jeu de travail maximal, en octets, pour le processus en cours de profilage](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|Ce message signale la quantité maximale de mémoire physique, en octets, que le processus utilisait lorsque le profilage était actif.|  
|[DA0505 : nombre moyen d'octets privés alloués pour le processus en cours de profilage](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|Ce message signale la quantité moyenne de mémoire virtuelle, en octets, que le processus allouait lorsque le profilage était actif.  Cette mesure de mémoire virtuelle est appelée *octets privés*.  Octets privés représente les emplacements de mémoire virtuelle alloués par le processus et accessibles uniquement par les threads en cours d'exécution dans le processus.|  
|[DA0506 : nombre maximal d'octets privés alloués pour le processus en cours de profilage](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|Ce message signale la quantité maximale de mémoire virtuelle que le processus allouait en octets privés lorsque le profilage était actif.|