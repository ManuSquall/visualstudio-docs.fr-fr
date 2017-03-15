---
title: "Mode R&#233;sum&#233; - donn&#233;es d&#39;instrumentation du profileur | Microsoft Docs"
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
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Mode R&#233;sum&#233; - donn&#233;es d&#39;instrumentation du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le mode Résumé affiche des informations sur les fonctions les plus performantes dans une exécution de profilage.  Pour plus d'informations, y compris une description des liens de notification et des listes de rapports, consultez [Mode Résumé](../profiling/summary-view.md).  
  
## Graphique de chronologie  
 Le graphique de chronologie du mode Résumé affiche l'utilisation du processeur par l'application profilée pendant le temps de profilage.  Vous pouvez utiliser le graphique de chronologie pour filtrer la vue selon un intervalle de temps sélectionné.  Pour plus d’informations, consultez [Comment : filtrer les vues de rapport à partir de la chronologie Résumé](../Topic/How%20to:%20Filter%20Report%20Views%20from%20the%20Summary%20Timeline.md).  
  
## Chemin réactif  
 Le **Chemin réactif** affiche le chemin d'exécution qui a exigé le plus de temps.  Vous pouvez cliquer sur une fonction pour afficher la vue Informations relatives à la fonction pour la fonction.  Pour consulter d'autres vues pour la fonction, cliquez avec le bouton droit sur la fonction, puis cliquez sur une vue dans la liste.  
  
 Le **chemin réactif** inclut les données suivantes pour chaque fonction :  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Name**|Nom de la fonction.|  
|**Temps inclusif écoulé en %**|Pourcentage de tout le temps contenu dans les données de profilage que la fonction a passé à exécuter du code dans son corps de fonction et dans les fonctions qu'elle a appelées.|  
|**Temps exclusif écoulé en %**|Pourcentage de tout le temps contenu dans les données de profilage que la fonction a passé à exécuter du code dans son corps de fonction.  Le temps passé dans les fonctions appelées par la fonction n'est pas inclus.|  
  
## Fonctions exigeant le plus de travail individuel  
 Liste des fonctions qui ont exigé le plus de temps pour exécuter le code dans le corps de la fonction et pas dans les fonctions qu'elles ont appelées.  
  
 Les **Fonctions exigeant le plus de travail individuel** incluent les données suivantes pour chaque fonction :  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Name**|Nom de la fonction.|  
|**Temps exclusif %**|Pourcentage de tout le temps contenu dans les données de profilage que la fonction a passé à exécuter du code dans son corps de fonction.  Le temps passé dans les fonctions appelées par la fonction n'est pas inclus.|  
  
## Voir aussi  
 [Mode Résumé](../profiling/summary-view-sampling-data.md)   
 [Mode Résumé](../profiling/summary-view-dotnet-memory-data.md)