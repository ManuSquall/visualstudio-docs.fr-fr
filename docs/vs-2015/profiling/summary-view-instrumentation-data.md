---
title: Vue Résumé - Données d’instrumentation | Microsoft Docs
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
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17534c0c7970238d4b6ef3de79c87d637743ff83
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493156"
---
# <a name="summary-view---instrumentation-data"></a>Vue Résumé - Données d’instrumentation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [vue Résumé - données d’Instrumentation](https://docs.microsoft.com/visualstudio/profiling/summary-view-instrumentation-data).  
  
La vue Résumé affiche des informations sur les fonctions dont le coût est le plus élevé quant aux performances dans une exécution du profilage. Pour plus d’informations, notamment une description des liens de notification et des listes de rapports, consultez [Vue Résumé](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Graphique chronologique  
 Le graphique chronologique de la vue Résumé montre l’utilisation du processeur (UC) par application profilée pendant la durée du profilage. Vous pouvez utiliser le graphique chronologique pour filtrer la vue en lui appliquant un intervalle de temps sélectionné. Pour plus d’informations, consultez [Guide pratique pour filtrer les vues de rapport à partir de la chronologie Résumé](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="hot-path"></a>Chemin réactif  
 Le **chemin réactif** montre le chemin d’exécution qui a consommé le plus de temps. Vous pouvez cliquer sur une fonction pour afficher la vue Détails de la fonction pour celle-ci. Pour afficher d’autres vues pour la fonction, cliquez avec le bouton droit sur la fonction, puis cliquez sur une vue de la liste.  
  
 Le **chemin réactif** inclut les données suivantes pour chaque fonction :  
  
|Colonne|Description|  
|------------|-----------------|  
|**Name**|Nom de la fonction.|  
|**% de temps inclusif écoulé**|Pourcentage du temps total dans les données de profilage que la fonction a passé à exécuter du code dans son corps de fonction et dans les fonctions qu’elle a appelées.|  
|**% de temps exclusif écoulé**|Pourcentage du temps total dans les données de profilage que la fonction a passé à exécuter du code dans son corps de fonction. Le temps passé dans les fonctions appelées par la fonction n’est pas inclus.|  
  
## <a name="functions-with-most-individual-work"></a>Fonctions avec le plus de travail individuel  
 Liste des fonctions qui consommé le plus de temps à exécuter du code dans le corps de la fonction et pas dans les fonctions appelées.  
  
 **Fonctions avec plus de travail individuel** inclut les données suivantes pour chaque fonction :  
  
|Colonne|Description|  
|------------|-----------------|  
|**Name**|Nom de la fonction.|  
|**% de durée exclusive**|Pourcentage du temps total dans les données de profilage que la fonction a passé à exécuter du code dans son corps de fonction. Le temps passé dans les fonctions appelées par la fonction n’est pas inclus.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Résumé](../profiling/summary-view-sampling-data.md)   
 [Vue Résumé](../profiling/summary-view-dotnet-memory-data.md)



