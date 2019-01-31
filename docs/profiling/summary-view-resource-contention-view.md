---
title: Vue Résumé - Vue Conflit de ressources | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 6da57b83-7b42-4d7c-9aea-8e0a830faf6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 32bd10c1260309856eba14a3a42d2acaac939f6e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55029217"
---
# <a name="summary-view---resource-contention-view"></a>Vue Résumé - Vue Conflit de ressources
La vue Résumé affiche des informations sur les événements de votre application dans lesquels un thread ou un processus a été interrompu dans l’attente de pouvoir à une ressource.  
  
 Pour plus d’informations, notamment une description des liens de notification et des listes de rapports, consultez [Vue Résumé](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Graphique chronologique  
 Le graphique chronologique de la vue Résumé montre le nombre d’événements de conflit de ressources de l’application profilée pendant la durée du profilage. Vous pouvez utiliser le graphique chronologique pour filtrer la vue en lui appliquant un intervalle de temps sélectionné. Pour plus d'informations, voir [Procédure : Filtrer les vues des rapports à partir de la chronologie Résumé](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="most-contended-resources"></a>Ressources présentant le plus de conflits  
 **Ressources présentant le plus de conflits** répertorie les ressources de l’application qui ont provoqué le plus d’événements de conflit. Vous pouvez cliquer sur un nom de ressource pour afficher la vue Conflits. La vue Conflits fournit une chronologie détaillée des conflits de ressources par thread.  
  
 **Ressources présentant le plus de conflits** inclut les données suivantes pour chaque ressource.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Name**|Nom de la ressource.|  
|**% de conflits**|Pourcentage de tous les événements de conflit dans les données de profilage qui étaient des conflits sur cette ressource.|  
  
## <a name="most-contended-thread"></a>Thread présentant le plus de conflits  
 **Threads présentant le plus de conflits** répertorie les threads dans l’application qui ont eu le plus grand nombre d’événements de conflit. Vous pouvez cliquer sur un nom de thread pour afficher la vue Conflits, qui fournit une chronologie détaillée des conflits de ressources dus au thread.  
  
 **Threads présentant le plus de conflits** inclut les données suivantes pour chaque thread.  
  
|Colonne|Description|  
|------------|-----------------|  
|**ID**|Identificateur du thread.|  
|**Name**|Nom du processus propriétaire du thread.|  
|**% de conflits**|Pourcentage de tous les événements de conflit dans les données de profilage qui étaient des conflits sur cette ressource.|