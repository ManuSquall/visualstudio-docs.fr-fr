---
title: "Vue Modules - Données de conflit | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Modules view
ms.assetid: 1a9aa122-2d8f-4a09-b503-92975aa6b648
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5503422ece5847018e8d321dba9cf674dff9e623
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="modules-view---contention-data"></a>Vue Modules - Données de conflit
La vue Modules des données de conflit affiche les données de concurrence regroupées selon les modules qui ont été échantillonnés dans les données de profilage. Chaque module est la racine d’une arborescence hiérarchique. Les fonctions du module dans lequel les événements de concurrence se sont produits sont répertoriés sous le nœud du module.  
  
 Si la fonction exécutait son propre code quand un événement de conflit s’est produit (autrement dit, si elle était en haut de la pile des appels), les lignes sources et les adresses des instructions qui s’exécutaient sont répertoriées sous le nœud de la fonction. Comme les données sont collectées pour une ligne source ou un pointeur d’instruction quand la ligne ou l’instruction est en cours d’exécution, les valeurs inclusives et exclusives sont toujours les mêmes pour les données de ligne et les données d’instruction.  
  
 Le tableau suivant décrit les valeurs des colonnes de la vue Modules des données de conflit.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps bloqué exclusif**|-   Pour une fonction, durée pendant laquelle l’exécution du code du corps de cette fonction a été bloquée. Le temps bloqué dans les fonctions qui ont été appelées par la fonction n’est pas inclus.<br />-   Pour un module, somme des durées de blocage exclusives des fonctions du module.<br />-   Pour une ligne ou une instruction, durée pendant laquelle l’exécution de cette ligne ou de cette instruction a été bloquée.|  
|**% de temps bloqué exclusif**|-   Pour une fonction ou un module, pourcentage de la durée totale de blocage dans l’exécution du profilage qui était du temps de blocage exclusif de cette fonction ou de ce module.<br />-   Pour une ligne ou une instruction, pourcentage de la durée totale de blocage dans l’exécution du profilage pendant lequel l’exécution de cette ligne ou de cette instruction a été bloquée.|  
|**Conflits exclusifs**|-   Pour une fonction, nombre de fois où l’exécution de code du corps de la fonction a été bloquée. Les conflits dans les fonctions qui ont été appelées par la fonction ne sont pas incluses.<br />-   Pour un module, somme des conflits exclusifs des fonctions dans le module.<br />-   Pour une ligne ou une instruction, nombre de fois où l’exécution de cette ligne ou de cette instruction a été bloquée.|  
|**% de conflits exclusifs**|-   Pour une fonction ou un module, pourcentage de tous les conflits dans l’exécution du profilage qui étaient des conflits exclusifs de cette fonction ou de ce module.<br />-   Pour une ligne ou une instruction, pourcentage de tous les conflits dans l’exécution du profilage qui étaient des conflits ayant bloqué l’exécution de cette ligne ou de cette instruction.|  
|**Temps bloqué inclusif**|-   Pour une fonction, durée pendant laquelle l’exécution de cette fonction ou d’une des fonctions appelées par cette fonction a été bloquée.<br />-   Pour un module, somme du temps de blocage pendant lequel au moins une fonction du module était sur la pile.<br />-   Pour une ligne ou une instruction, durée pendant laquelle l’exécution de cette ligne ou de cette instruction a été bloquée.|  
|**% de temps bloqué inclusif**|-   Pour une fonction ou un module, pourcentage de la durée totale de blocage dans l’exécution du profilage qui était du temps de blocage inclusif de cette fonction ou de ce module.<br />-   Pour une ligne ou une instruction, pourcentage de la durée totale de blocage dans l’exécution du profilage pendant lequel cette ligne ou cette instruction s’exécutait.|  
|**Conflits inclusifs**|-   Pour une fonction, nombre de fois où l’exécution de cette fonction ou d’une des fonctions appelées par cette fonction a été bloquée.<br />-   Pour un module, nombre de conflits dans lesquels au moins une fonction de ce module était sur la pile.<br />-   Pour une ligne ou une instruction, nombre de fois où l’exécution de cette ligne ou de cette instruction a été bloquée.|  
|**% de conflits inclusifs**|-   Pour une fonction ou un module, pourcentage de tous les conflits dans l’exécution du profilage qui étaient des conflits inclufs de cette fonction ou de ce module.<br />-   Pour une ligne ou une instruction, pourcentage de la durée totale de blocage dans l’exécution du profilage pendant lequel cette ligne ou cette instruction s’exécutait.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Nom du module**|Nom du module qui contient la fonction, la ligne ou le pointeur d’instruction.|  
|**Chemin du module**|Chemin du module qui contient le module, la fonction, la ligne ou le pointeur d’instruction.|  
|**Name**|Nom du module ou de la fonction.|  
|**ID du processus**|ID du processus (PID) de l'exécution du profilage.|  
|**Nom du processus**|Nom du processus.|  
|**Fichier source**|Fichier source contenant la définition pour cette fonction.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour personnaliser les colonnes de la vue Rapport](../profiling/how-to-customize-report-view-columns.md)   
 [Vue Modules - Données d’instrumentation](../profiling/modules-view.md)   
 [Modules, vue - Instrumentation](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Vue Modules - Échantillonnage](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Vue Modules - Données d’instrumentation](../profiling/modules-view-instrumentation-data.md)   
 [Vue Modules - Données d’échantillonnage](../profiling/modules-view-sampling-data.md)