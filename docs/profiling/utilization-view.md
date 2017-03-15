---
title: "vue Utilisation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.cpuutilization"
helpviewer_keywords: 
  - "visualiseur concurrentiel, vue Utilisation de l’UC"
ms.assetid: b4f7ceab-3653-4069-bb74-c309aec62866
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# vue Utilisation
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La **Vue utilisation** affiche des informations sur le processeur, le GPU, et d'autres ressources système qui sont utilisées par le processus actuel.  Elle affiche l'utilisation principale moyenne par le processus analysé, le processus inactif, le processus système et d'autres processus qui s'exécutent sur le système au fil du temps.  Elle n'indique pas quel cœur spécifique est actif à un moment donné.  Par exemple, si deux cœurs s'exécutent chacun à 50 % de leur capacité pendant une période donnée, cette vue affiche un seul cœur logique en cours d'utilisation.  La vue est générée en décomposant la durée du profilage en intervalle de temps courts.  Pour chaque segment, le graphique indique le nombre moyen de threads de processus qui s'exécutent sur les cœurs logiques pendant cet intervalle.  
  
 ![Utilisation de l’UC, vue](../profiling/media/vsts_ppacpuutil.png "VSTS\_PPAcpuUtil")  
  
 Le graphique affiche le temps \(sur l'axe des x\) et les cœurs logiques moyen utilisés par le processus cible, les processus en attente, et le processus système. \(Le processus en attente affiche les cœurs inactifs.  Le processus système est un processus dans windows qui peuvent effectuer le travail de la part d'autres processus.\) Les processus restants qui s'exécutent sur le compte système pour l'utilisation de tous les cœurs restants.  
  
 Le nombre de cœurs logiques est indiqué sur l'axe des Y.  Le système d'exploitation Windows traite simultanément la prise en charge du multithreading dans le matériel comme des cœurs logiques \(par exemple, Hyper\-Threading\).  Par conséquent, un système doté d'un processeur quadricœur qui prend en charge deux threads matériels par cœur apparaît comme un système à huit cœurs logiques.  Cela s'applique également à la Vue Cœurs.  Pour plus d'informations, consultez [Affichage Cœurs](../profiling/cores-view.md).  
  
 Le graphique d'activités GPU indique le nombre de moteurs DirectX en service dans le temps.  Un moteur est utilisé s'il traite un pack d'accès direct à la mémoire.  Le graphique n'affiche pas le moteur spécifique DirectX \(par exemple, le moteur du moteur 3D et visuelle, et les autres\).  
  
## Objectif  
 Nous recommandons la vue Utilisation comme point de départ pour les examens de performances lors de l'utilisation du Visualiseur concurrentiel.  Comme il fournit une vue d'ensemble du degré d'accès concurrentiel dans une application au fil du temps, vous pouvez l'utiliser pour identifier rapidement les zones qui requièrent un réglage des performances ou de la parallélisation.  
  
 Si vous êtes intéressé par le réglage des performances, vous pouvez essayer d'identifier un comportement qui ne répond pas à vos attentes.  Vous pouvez également chercher l'existence et la cause des régions qui ont une faible utilisation des cœurs d'UC logiques.  Vous pouvez également rechercher des modèles d'utilisation entre le processeur et le GPU.  
  
 Si vous êtes intéressé par la parallélisation d'une application, vous rechercherez probablement soit des zones d'exécution utilisant le processeur de manière intensive, soit des zones où le processeur n'est pas utilisé.  
  
 Les zones utilisant le processeur de manière intensive sont vertes.  Le graphique affiche un cœur utilisé si l'application est séquentielle.  
  
 Les zones où le processeur n'est pas utilisé sont grises.  Celles\-ci peuvent représenter des moments auxquels l'application est inactive ou exécute des E\/S bloquantes qui fournissent des possibilités de parallélisme en se chevauchant avec d'autres activités utilisant le processeur de manière intensive.  
  
 Lorsque vous recherchez un comportement d'intérêt, vous pouvez effectuer un zoom avant sur cette zone en la sélectionnant.  Après avoir zoomé, vous pouvez basculer vers la vue Threads ou la vue Cœurs pour lancer une analyse plus détaillée.  
  
 Si vous utilisez le GPU à l'aide de C\+\+ AMP ou DirectX, vous pouvez être intéressé d'identifier le nombre des moteurs de GPU en service ou de zones où le GPU est inactif de façon inattendue.  
  
## Zoom  
 Pour effectuer un zoom avant sur le graphique d'utilisation de l'UC ou le graphique d'activités de GPU, sélectionnez une section ou utilisez le curseur de zoom au\-dessus du graphique.  Le paramètre de zoom est maintenu lorsque vous basculez vers d'autres vues.  Pour effectuer un zoom arrière, utilisez le curseur du zoom.  Vous pouvez également effectuer un zoom à l'aide de Ctrl\+scroll.  
  
## Voir aussi  
 [Visualiseur concurrence](../profiling/concurrency-visualizer.md)   
 [Affichage Cœurs](../profiling/cores-view.md)