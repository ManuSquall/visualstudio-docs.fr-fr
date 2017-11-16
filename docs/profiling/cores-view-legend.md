---
title: "Légende de la vue Cœurs | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.cores.legend
helpviewer_keywords: Concurrency Visualizer, Cores View Legend
ms.assetid: e160384c-fcfe-49b3-86b7-229adb736c51
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 820c5c48b9fc3b8d05d6e4d867e198ecc9237634
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="cores-view-legend"></a>Légende de la vue Cœurs
La légende de la vue Cœurs identifie chaque thread par couleur et par nom. Elle comprend des colonnes qui contiennent des valeurs pour les changements de contexte inter-cœurs, le total de changements de contexte et le pourcentage de changements de contexte inter-cœurs. Les lignes de la légende sont triées selon le nombre de changements de contexte inter-cœurs, dans l’ordre décroissant.  
  
 Vous pouvez sélectionner des lignes de la légende pour filtrer les threads qui doivent s’afficher dans la chronologie. Seuls les threads sélectionnés sont affichés dans la chronologie. Si aucune ligne n’est sélectionnée, toutes les lignes apparaîtront dans la chronologie.  
  
 Les changements de contexte inter-cœurs coûtent davantage en surcharge et en performances que les changements qui restent sur le même cœur logique. Pendant un changement de contexte, les registres du processeur sont enregistrés et restaurés, le code du noyau du système d’exploitation est exécuté, les entrées de mémoire du tampon de traduction sont rechargées et le pipeline du processeur est vidé. Les changements de contexte inter-cœurs peuvent être encore plus coûteux que les autres changements de contexte, car les données du cache ne sont pas valides pour ce thread sur un autre cœur. En revanche, si un thread change de contexte vers un cœur sur lequel il s’est exécuté précédemment, il est probable que les données utiles soient toujours dans le cache. Lorsque des changements de contexte inter-cœurs augmentent en raison de tentatives de gestion de l’affinité de thread et que les performances se dégradent, envisagez de résoudre ce problème. Commencez par éliminer l’affinité de thread, puis observez le comportement inter-cœurs qui en résulte.  
  
 Le tableau ci-dessous décrit les éléments de la légende.  
  
|Élément|Définition|  
|-------------|----------------|  
|Nom du thread|Affiche la couleur du thread dans la chronologie de cœurs précédente, ainsi que le nom du thread.|  
|Changements de contexte inter-cœurs|Nombre de changements de contexte pour un thread qui est également passé d’un cœur logique à un autre. Aucune différence n’est faite entre les changements de contexte inter-cœurs qui passent d’une matrice de processeur à l’autre, et ceux qui restent sur la même matrice.|  
|Changements de contexte totaux|Nombre total de changements de contexte pour un thread donné pendant la période d’échantillonnage. Chaque fois qu’un thread change de contexte (par exemple, de l’exécution à la synchronisation), un changement de contexte est comptabilisé.|  
|Pourcentage de changements de contexte inter-cœurs|Calculé comme un pourcentage en divisant le nombre de changements de contexte inter-cœurs par le nombre total de changements de contexte. Plus ce pourcentage est élevé, plus l’impact global de la surcharge des changements de contexte inter-cœurs affectera les performances du thread en question.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Cœurs](../profiling/cores-view.md)