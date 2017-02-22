---
title: "Graphique d&#39;activit&#233; GPU | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.cpu.graph.gpu"
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Graphique d&#39;activit&#233; GPU
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le graphique d'activités GPU dans le Visualiseur concurrentiel affiche le niveau de l'activité DirectX sur le système tel que mesuré par le nombre de moteurs DirectX en cours d'utilisation au fil du temps.  Le graphique n'affiche pas quels moteurs spécifiques ont été utilisées.  Un moteur est considérée comme actif s'il traite n'importe quel travail GPU.  
  
## Couleurs du Graphique d'activités du GPU  
 Vert indique la consommation des moteurs de DirectX par le processus actuel.  
  
 Gris clair indique la consommation des moteurs de DirectX par d'autres processus sur le système.  Pour réduire la consommation des moteurs DirectX par d'autres processus, réduisez le nombre d'autres processus qui s'exécutent sur le système.  
  
 Le blanc indique la disponibilité des moteurs inutilisées DirectX sur le système.  Ces moteurs sont disponibles pour votre processus si vous trouvez plus d'occasions de les exploiter.  Les moteurs peuvent être utilisés pour des types de tâches spécifiques.  
  
## Voir aussi  
 [vue Utilisation](../profiling/utilization-view.md)