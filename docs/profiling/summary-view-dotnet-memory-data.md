---
title: "Mode R&#233;sum&#233; - donn&#233;es de la m&#233;moire .NET du profileur | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Mode Résumé"
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Mode R&#233;sum&#233; - donn&#233;es de la m&#233;moire .NET du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le mode Résumé affiche les informations à propos des fonctions et des types .NET qui ont alloué le plus de mémoire, et les types créés le plus grand nombre de fois au cours d'une exécution du profilage.  Pour plus d'informations, y compris une description des liens de notification et des listes de rapports, consultez [Mode Résumé](../profiling/summary-view.md).  
  
## Graphique de chronologie  
 Le graphique de chronologie du mode Résumé affiche l'utilisation du processeur par l'application profilée pendant le temps de profilage.  Vous pouvez utiliser le graphique de chronologie pour filtrer la vue selon un intervalle de temps sélectionné.  Pour plus d'informations, consultez [Comment : filtrer les vues de rapport à partir de la chronologie Résumé](../Topic/How%20to:%20Filter%20Report%20Views%20from%20the%20Summary%20Timeline.md).  
  
## Fonctions allouant le plus de mémoire  
 Répertorie les fonctions qui allouent le plus grand nombre d'octets de mémoire au cours de l'exécution du profilage.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Nom**|Nom de la fonction.|  
|**% d'octets**|Pourcentage de tous les octets alloués au cours de l'exécution du profilage qui ont été alloués par cette fonction ou par une fonction enfant appelée par cette fonction.|  
  
## Types ayant le plus de mémoire allouée  
 Répertorie les types pour lesquels le plus grand nombre d'octets de mémoire a été alloué au cours de l'exécution du profilage.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Nom**|Nom du type.|  
|**% d'octets**|Pourcentage de tous les octets alloués lors de l'exécution du profilage qui ont été alloués pour ce type.|  
  
## Types ayant le plus d'instances  
 Répertorie les types créés le plus grand nombre de fois au cours de l'exécution du profilage.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Nom**|Nom du type.|  
|**% d'instances**|Pourcentage du nombre total d'objets .NET créés lors de l'exécution du profilage qui étaient des instances de ce type.|  
  
## Voir aussi  
 [Mode Résumé](../profiling/summary-view-sampling-data.md)   
 [Mode Résumé](../profiling/summary-view-instrumentation-data.md)