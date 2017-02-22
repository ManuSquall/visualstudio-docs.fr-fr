---
title: "L&#233;gende de l’affichage Cœurs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.cores.legend"
helpviewer_keywords: 
  - "Visualiseur concurrentiel, légende de l’affichage Cœurs"
ms.assetid: e160384c-fcfe-49b3-86b7-229adb736c51
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# L&#233;gende de l’affichage Cœurs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La légende de la vue Cœurs identifie chaque thread par couleur et par nom.  Elle inclut des colonnes qui affichent des nombres correspondant aux changements de contexte inter\-cœurs, au nombre total de changements de contexte et au pourcentage de changements de contexte inter\-cœurs.  Les lignes de la légende sont triées en fonction du nombre de changements de contexte inter\-cœurs, dans un ordre décroissant.  
  
 Vous pouvez sélectionner des lignes dans la légende pour filtrer les threads affichés dans la chronologie.  Seuls les threads sélectionnés s'affichent dans la chronologie.  Si aucune ligne n'est sélectionnée, toutes les lignes sont affichées dans la chronologie.  
  
 Les changements de contexte inter\-cœurs sont plus onéreux en termes de frais généraux et en performances que les changements qui restent sur le même cœur logique.  Pendant les changements de contexte, les registres de processeur sont enregistrés et restaurés, le code noyau du du système d'exploitation est exécuté, les entrées de la traduction d'adresse du mémoire tampon sont rechargées, et le pipeline du processeur est vidé.  Les changements de contexte inter\-cœurs peuvent être encore plus coûteux que d'autres changements de contexte car les données de cache ne sont pas valides pour ce thread sur un autre cœur.  En revanche, si un thread est contextuellement basculé sur le cœur sur lequel il a précédemment été exécutée, il est probable que des informations utiles sont toujours dans le cache.  Lorsque le nombre de changements de contexte inter\-cœurs a été augmenté par des tentatives de gérer l'affinité de thread et que la performance est degradée, envisager la possibilité de traiter ce problème.  Commencez par supprimer l'affinité de thread, puis observez le comportement résultant entre les cœurs.  
  
 Le tableau suivant décrit les différents éléments de la légende.  
  
|Élément|Définition|  
|-------------|----------------|  
|Nom du thread|Affiche la couleur et le nom du thread dans la chronologie de cœurs précédente.|  
|Changements de contexte inter\-cœurs|Nombre de changements de contexte pour un thread qui est également passé d'un cœur logique à un autre.  Il ne fait pas la distinction entre les changements de contexte inter\-cœurs qui vont d'une puce de processeur à une autre, et ceux qui restent sur la même puce.|  
|Total de changements de contexte|Nombre total de changements de contexte pour un thread donné pendant la période d'échantillonnage.  Chaque fois qu'un thread change de contexte \(par exemple, de l'exécution à la synchronisation\) un changement de contexte est comptabilisé.|  
|Pourcentage de changements de contexte inter\-cœurs|Calculé comme un pourcentage, en divisant le nombre de changements de contexte inter\-cœurs par le nombre total de changements de contexte.  Plus ce pourcentage est élevé, plus l'impact global des charges des changements de contexte inter\-cœurs sur les performances de ce thread particulier est important.|  
  
## Voir aussi  
 [Affichage Cœurs](../profiling/cores-view.md)