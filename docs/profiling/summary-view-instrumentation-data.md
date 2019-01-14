---
title: Vue Résumé - Données d’instrumentation | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c54518701c2c57bd4a651c050e69e42307f8fdd8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952246"
---
# <a name="summary-view---instrumentation-data"></a>Vue Résumé - Données d’instrumentation
La vue Résumé affiche des informations sur les fonctions dont le coût est le plus élevé quant aux performances dans une exécution du profilage. Pour plus d’informations, notamment une description des liens de notification et des listes de rapports, consultez [Vue Résumé](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Graphique chronologique  
 Le graphique chronologique de la vue Résumé montre l’utilisation du processeur (UC) par application profilée pendant la durée du profilage. Vous pouvez utiliser le graphique chronologique pour filtrer la vue en lui appliquant un intervalle de temps sélectionné. Pour plus d'informations, voir [Procédure : Filtrer les vues des rapports à partir de la chronologie Résumé](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
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
 [Vue Résumé - Données d’échantillonnage](../profiling/summary-view-sampling-data.md)   
 [Vue Résumé - Données de la mémoire .NET](../profiling/summary-view-dotnet-memory-data.md)