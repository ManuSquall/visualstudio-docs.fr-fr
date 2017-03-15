---
title: "Mode R&#233;sum&#233; - vue des conflits de ressources du profileur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Mode Résumé"
ms.assetid: 6da57b83-7b42-4d7c-9aea-8e0a830faf6b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Mode R&#233;sum&#233; - vue des conflits de ressources du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le mode Résumé affiche les informations sur les événements dans votre application dans laquelle un thread ou un processus a été interrompu tandis qu'il attendait l'accès à une ressource.  
  
 Pour plus d'informations, y compris une description des liens de notification et des listes de rapports, consultez [Mode Résumé](../profiling/summary-view.md).  
  
## Graphique de chronologie  
 Le graphique de chronologie dans le mode Résumé affiche le nombre d'événements de conflit de l'application profilée pendant la durée du profilage.  Vous pouvez utiliser le graphique de chronologie pour filtrer la vue selon un intervalle de temps sélectionné.  Pour plus d’informations, consultez [Comment : filtrer les vues de rapport à partir de la chronologie Résumé](../Topic/How%20to:%20Filter%20Report%20Views%20from%20the%20Summary%20Timeline.md).  
  
## Ressources présentant le plus de conflits  
 **Ressources présentant le plus de conflits** répertorie les ressources dans l'application qui a provoqué le plus d'événements de conflit.  Vous pouvez cliquer sur un nom de ressource pour afficher le mode Conflits.  Le mode Conflits fournit une chronologie détaillée des conflits de ressources par thread.  
  
 **Ressources présentant le plus de conflits** incluent les données suivantes pour chaque ressource.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Name**|Nom de la ressource.|  
|**% de conflits**|Pourcentage de tous les événements de conflit dans les données de profilage qui étaient des conflits sur cette ressource.|  
  
## Threads présentant le plus de conflits  
 **Threads présentant le plus de conflits** répertorie les threads dans l'application qui avaient le plus grand nombre d'événements de conflit.  Vous pouvez cliquer sur un nom de thread pour afficher le mode Conflits qui fournit une chronologie détaillée des conflits de ressources par le thread.  
  
 **Threads présentant le plus de conflits** incluent les données suivantes pour chaque thread.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**ID**|Identificateur du thread.|  
|**Name**|Nom du processus qui est propriétaire du thread.|  
|**% de conflits**|Pourcentage de tous les événements de conflit dans les données de profilage qui étaient des conflits sur cette ressource.|