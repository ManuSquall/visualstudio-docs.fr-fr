---
title: Visualiseur concurrentiel | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.viewnavigation
- vs.cv.overview
- vs.cv.performance.gettingstarted
- vs.cv.gettingstarted
helpviewer_keywords:
- Concurrency Visualizer, Concurrency Visualizer
ms.assetid: ae5879a0-1e1a-455a-ba72-148e57f59289
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7c86228d21323d1928acb9fc94582fbb9d320248
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60084841"
---
# <a name="concurrency-visualizer"></a>Visualiseur concurrentiel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

REMARQUE]
>  Le visualiseur concurrentiel est une extension facultative de Visual Studio. Vous pouvez télécharger le visualiseur concurrentiel et les Outils de collecte du visualiseur concurrentiel à partir des liens suivants :  
> 
> - Télécharger l’extension              [Visualiseur concurrentiel](https://visualstudiogallery.msdn.microsoft.com/a6c24ce9-beec-4545-9261-293061436ee9) .  
>   - Télécharger les              [Outils de collecte du visualiseur concurrentiel pour Visual Studio 2015](http://www.microsoft.com/download/details.aspx?id=49103).  
> 
>   [L’utilitaire en ligne de commande du visualiseur concurrentiel (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md) permet de recueillir des traces à partir de la ligne de commande que vous pouvez afficher dans le visualiseur concurrentiel pour Visual Studio 2015. Vous pouvez utiliser cet outil sur des ordinateurs sur lesquels Visual Studio n’est pas installé.  
  
 Le visualiseur concurrentiel vous permet de voir comment votre application multithread s’exécute. Les vues du visualiseur concurrentiel fournissent des données graphiques, tabulaires et textuelles qui montrent les relations temporelles entre les threads de votre programme et le système en général. Vous pouvez utiliser le visualiseur concurrentiel pour localiser les goulots d’étranglement au niveau des performances, la sous-utilisation de l’UC, les conflits de threads, la migration de threads inter-cœurs, les délais de synchronisation, l’activité DirectX, les zones d’E/S avec chevauchement et d’autres informations. Les vues fournissent des données exploitables en liant leur sortie graphique aux piles des appels et au code source.  
  
 Le visualiseur concurrentiel s’appuie sur la fonctionnalité [Suivi d’événements pour Windows](http://go.microsoft.com/fwlink/?LinkId=234579) .  
  
> [!NOTE]
>  Le visualiseur concurrentiel ne prend pas en charge les projets web.  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Vue Utilisation](../profiling/utilization-view.md)|Explique comment consulter et analyser l’activité système sur tous les processeurs.|  
|[vue Threads](../profiling/threads-view-parallel-performance.md)|Explique comment analyser les interactions entre les threads dans votre programme.|  
|[Vue Cœurs](../profiling/cores-view.md)|Explique comment analyser la migration de threads entre les cœurs.|  
|[Modèles courants pour des applications multithread au comportement médiocre](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|Décrit plusieurs modèles courants et indique comment ils apparaissent dans le visualiseur concurrentiel.|  
|[Blog Parallel Development in Visual Studio](http://go.microsoft.com/fwlink/?LinkId=235385)|Fournit des conseils et les meilleures pratiques pour le visualiseur concurrentiel.|  
|[Vues du rapport des performances](../profiling/performance-report-views.md)|Cette section fournit des informations de référence pour les rapports et les vues des outils de profilage de Visual Studio.|  
|[Kit SDK du visualiseur concurrentiel](../profiling/concurrency-visualizer-sdk.md)|Décrit comment instrumenter votre code source pour afficher des informations supplémentaires dans le visualiseur concurrentiel.|  
|[Utilitaire en ligne de commande du visualiseur concurrentiel (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|Décrit comment utiliser l’utilitaire de ligne de commande du visualiseur concurrentiel (CVCollectionCmd.exe) pour collecter et traiter les traces sur les ordinateurs qui n’ont pas Visual Studio.|  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de profilage](../profiling/profiling-tools.md)
