---
title: "Affichage Cœurs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.cores"
helpviewer_keywords: 
  - "Visualiseur concurrentiel, affichage Cœurs"
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Affichage Cœurs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vue Cœurs montre comment l'exécution du thread a été mappée aux cœurs de processeurs logiques.  Si vous écrivez des applications serveur, cette vue peut vous aider à optimiser la performance du cache grâce à la gestion d'affinité de thread ou de pool de thread.  Elle peut également vous aider à examiner des cas où l'utilisation de l'affinité de thread a peut\-être aggravé le problème de migration intercœurs.  La vue Cœurs a deux parties, un graphique et une légende.  
  
 Le graphique représente les cœurs logiques sur l'axe y et le temps sur l'axe x.  Chaque thread du graphique a une couleur unique afin que vous puissiez suivre le déplacement intercœurs de chaque thread dans le temps.  Vous pouvez filtrer les threads dans ce graphique en les sélectionnant dans la zone de légende.  
  
 La zone de légende a une entrée pour chaque couleur dans le graphique.  Chaque entrée indique la couleur et le nom de thread, le nombre de changements de contexte intercœurs, le nombre total de changements de contexte et le pourcentage de changements de contexte intercœurs.  La légende est triée en fonction du nombre de changements de contexte inter\-cœurs, dans un ordre décroissant.  Elle répertorie uniquement les threads qui ont exécuté pendant la plage horaire affichée.  La liste est mise à jour si vous zoomez ou filtrer.  
  
## Voir aussi  
 [Visualiseur concurrence](../profiling/concurrency-visualizer.md)   
 [vue Utilisation](../profiling/utilization-view.md)   
 [vue Threads](../profiling/threads-view-parallel-performance.md)