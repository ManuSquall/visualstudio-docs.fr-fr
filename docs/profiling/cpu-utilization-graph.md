---
title: "Graphique d’utilisation du processeur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.cpu.graph"
helpviewer_keywords: 
  - "graphique d’utilisation du processeur (visualiseur concurrentiel), graphique d’utilisation du processeur"
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Graphique d’utilisation du processeur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le graphique d'utilisation de l'UC indique le niveau d'utilisation dans une application au fil du temps.  L'axe des abscisses représente la durée de la trace et l'axe des ordonnées correspond au nombre de cœurs logiques sur le système.  Le graphique n'indique pas quel cœur spécifique est actif à un moment donné.  Par exemple, si deux cœurs s'exécutent chacun à 50 % de leur capacité pendant une période donnée, cette vue affiche un seul cœur logique en cours d'utilisation.  
  
## Couleurs du graphique de l'utilisation de l'UC  
  
-   Vert indique l'utilisation des cœurs logiques sur le système par le processus actuel.  
  
-   Gris clair indique l'utilisation des cœurs logiques par d'autres processus sur le système.  Un pourcentage élevé de gris clair dans le graphique indique que le système est lourdement chargé par d'autres processus et que votre processus est en passe d'être reporté par ces autres processus.  Pour réduire la consommation de cœurs logiques par d'autres processus, réduisez le nombre de ceux qui s'exécute sur le système.  
  
-   Le gris foncé indique la consommation de cœurs logiques par le processus système.  Vous ne pouvez pas le contrôler directement, mais il est particulièrement utile de savoir quand il se produit car il peut affecter la disponibilité des cœurs logiques de votre processus.  
  
-   Le blanc indique la disponibilité des cœurs logiques inutilisés sur le système.  Ces cœurs sont disponibles pour votre processus si vous pouvez rechercher plus de possibilités pour le parallélisme.  
  
## Voir aussi  
 [vue Utilisation](../profiling/utilization-view.md)   
 [Utilisation moyenne de l'UC](../profiling/average-cpu-utilization.md)