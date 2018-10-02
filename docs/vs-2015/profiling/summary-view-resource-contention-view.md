---
title: Vue Résumé - Vue Conflit de ressources | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Summary view
ms.assetid: 6da57b83-7b42-4d7c-9aea-8e0a830faf6b
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf83509cd56343001a94da619b9246464ed75bdf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493078"
---
# <a name="summary-view---resource-contention-view"></a>Vue Résumé - Vue Conflit de ressources
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [vue Résumé - vue conflit de ressources](https://docs.microsoft.com/visualstudio/profiling/summary-view-resource-contention-view).  
  
La vue Résumé affiche des informations sur les événements de votre application dans lesquels un thread ou un processus a été interrompu dans l’attente de pouvoir à une ressource.  
  
 Pour plus d’informations, notamment une description des liens de notification et des listes de rapports, consultez [Vue Résumé](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Graphique chronologique  
 Le graphique chronologique de la vue Résumé montre le nombre d’événements de conflit de ressources de l’application profilée pendant la durée du profilage. Vous pouvez utiliser le graphique chronologique pour filtrer la vue en lui appliquant un intervalle de temps sélectionné. Pour plus d’informations, consultez [Guide pratique pour filtrer les vues de rapport à partir de la chronologie Résumé](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
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



