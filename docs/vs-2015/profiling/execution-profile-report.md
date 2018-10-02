---
title: Profil d’exécution, rapport| Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.report.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Profile Report
ms.assetid: c8128472-a8ed-46f4-b1c8-a25358d6f2c1
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6e13e18857ce67bc5d333fb2d91b2df97fdc08d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503506"
---
# <a name="execution-profile-report"></a>Profil d’exécution, rapport
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [rapport de profil d’exécution](https://docs.microsoft.com/visualstudio/profiling/execution-profile-report).  
  
Le rapport Profil d’exécution est un profil d’échantillonnage classique. Des échantillons sont créés chaque milliseconde environ pendant des périodes où un thread s’exécute sur un cœur logique, et le visualiseur concurrentiel génère une arborescence des appels typique en assemblant les échantillons de piles accumulés. Les données de ce tableau peuvent être affectées par la plage horaire actuelle et les threads cachés, ainsi que par les filtres qui peuvent être appliqués :  
  
-   Si l’option Uniquement mon code est activée, seuls les frames de pile contenant du code utilisateur sont présentés, ainsi que le premier niveau situé sous le code utilisateur.  
  
-   Si la valeur Réduction du bruit est définie, les piles assemblées dont la fréquence est inférieure à celle spécifiée sont retirées du rapport.  
  
 Le tableau suivant montre les colonnes du rapport.  
  
|Colonne|Description|  
|------------|-----------------|  
|Name|Nom de la fonction pour chaque niveau de la pile des appels.|  
|Échantillons inclusifs|Nombre total d’échantillons collectés pour toutes les piles qui atteignent ce niveau de l’arborescence de la pile des appels. Le nombre inclusif correspond à la somme des échantillons exclusifs de cette fonction et des compteurs inclusifs de tous ses nœuds enfants.|  
|Exemples exclusifs|Nombre total d’échantillons collectés pour lesquels cette fonction correspond au niveau le plus bas de la pile des appels.|  
|% inclusif|Pourcentage du total des échantillons qui apparaissent dans la colonne des échantillons inclusifs. Les pourcentages sont arrondis à deux décimales.|  
|% exclusifs|Pourcentage du total des échantillons qui apparaissent dans la colonne des échantillons exclusifs. Les pourcentages sont arrondis à deux décimales.|  
|Détails|Nom complet de la fonction. Peut contenir le nombre de lignes lorsque celui-ci est disponible.|  
  
 Ce tableau peut être consulté dans la vue [Durée d’exécution (vue Threads)](../profiling/execution-time-threads-view.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Threads](../profiling/threads-view-parallel-performance.md)



