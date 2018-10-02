---
title: Vue Fonctions - Données d’instrumentation | Microsoft Docs
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
- Function view
ms.assetid: 595d91c8-a42b-4644-85b8-39e8140a5dfe
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c99ac53b5059877a7025d978439a8c3468640eb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47506890"
---
# <a name="functions-view---instrumentation-data"></a>Vue Fonctions - Données d’instrumentation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [mode fonctions - données d’Instrumentation](https://docs.microsoft.com/visualstudio/profiling/functions-view-instrumentation-data).  
  
La vue du rapport Fonctions répertorie les données de profilage par nom de fonction.  
  
## <a name="general"></a>Général  
 Les colonnes générales permettent d’identifier la fonction dans une ligne de la vue.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Nom de la fonction**|Nom de la fonction.|  
|**Adresse de la fonction**|Adresse de la fonction.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Nombre d’appels**|Nombre total d'appels passés à cette fonction.|  
|**Fichier source**|Fichier source contenant la définition pour cette fonction.|  
|**Nom du module**|Nom du module qui contient la fonction.|  
|**Chemin de module**|Chemin d’accès du module qui contient la fonction.|  
|**ID du processus**|ID du processus (PID) de l'exécution du profilage.|  
|**Nom du processus**|Nom du processus.|  
|**Traitement de sondes du temps exclusif**|Surcharge de temps pour cette fonction qui est provoquée par l'instrumentation. Cela n’inclut pas la surcharge des fonctions appelées par la fonction. Le traitement de sondes a été soustrait de tous les temps exclusifs.|  
|**Traitement des sondes temps inclus**|Surcharge de temps pour cette fonction et ses fonctions enfants qui est provoquée par l'instrumentation. Cela inclut la surcharge dans les fonctions appelées par la fonction. Le traitement de sondes a été soustrait de tous les temps inclusifs.|  
  
## <a name="elapsed-inclusive-values"></a>Valeurs de temps inclusif écoulé  
 Les valeurs de temps inclusif écoulé indiquent le temps qu’a passé une fonction dans la pile des appels. Cette durée comprend le temps passé dans les fonctions qui ont été appelées par la fonction, ainsi que les appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps inclusif écoulé**|Temps inclusif écoulé total de tous les appels à cette fonction.|  
|**% de temps inclusif écoulé**|Pourcentage du temps inclusif écoulé total de l’exécution de profilage passé dans le temps inclusif écoulé de cette fonction.|  
|**Temps inclusif écoulé moy.**|Temps inclusif écoulé moyen d’un appel à cette fonction.|  
|**Temps inclusif écoulé max.**|Temps inclusif écoulé maximal d’un appel à cette fonction.|  
|**Temps inclusif écoulé min.**|Temps inclusif écoulé minimal d’un appel à cette fonction.|  
  
## <a name="elapsed-exclusive-values"></a>Valeurs de temps exclusif écoulé  
 Les valeurs de temps exclusif écoulé indiquent la durée pendant laquelle une fonction a exécuté du code dans le corps de la fonction, c’est-à-dire, lorsque la fonction se trouvait en haut de la pile des appels. Cette durée comprend les appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S, mais ne comprend pas le temps passé dans les fonctions qui ont été appelées par la fonction.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps exclusif écoulé**|Temps exclusif écoulé total de tous les appels à cette fonction.|  
|**% de temps exclusif écoulé**|Pourcentage du temps exclusif écoulé total de l’exécution de profilage passé dans le temps exclusif écoulé total de cette fonction.|  
|**Temps exclusif écoulé moy.**|Temps exclusif écoulé moyen d’un appel à cette fonction.|  
|**Temps exclusif écoulé max.**|Temps exclusif écoulé maximal d’un appel à cette fonction.|  
|**Temps exclusif écoulé min.**|Temps exclusif écoulé minimal d’un appel à cette fonction.|  
  
## <a name="application-inclusive-values"></a>Valeurs de temps inclusif d’application  
 Les valeurs de temps inclusif d’application indiquent le temps qu’a passé une fonction dans la pile des appels. Cette durée ne comprend pas les appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S, mais elle comprend le temps passé dans les fonctions qui ont été appelées par la fonction.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps inclusif d’application**|Temps inclusif d’application total de tous les appels à cette fonction.|  
|**% du temps inclusif d’application**|Pourcentage du temps inclusif écoulé total de l’exécution de profilage passé dans le temps inclusif d’application total de cette fonction.|  
|**Temps inclusif d’application moy.**|Temps inclusif d’application moyen d’un appel à cette fonction.|  
|**Temps inclusif d’application max.**|Temps inclusif d’application maximal d’un appel à cette fonction.|  
|**Temps inclusif d’application min.**|Temps inclusif d’application minimal d’un appel à cette fonction.|  
  
## <a name="application-exclusive-values"></a>Valeurs de temps exclusif d’application  
 Les valeurs de temps exclusif d’application indiquent la durée pendant laquelle une fonction s’est exécutée directement en haut de la pile des appels. Cette durée ne comprend pas les appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S, ni le temps passé dans les fonctions qui ont été appelées par la fonction.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps exclusif d’application**|Temps exclusif d’application total de tous les appels à cette fonction.|  
|**% du temps exclusif d’application**|Pourcentage du temps exclusif écoulé total de l’exécution de profilage passé dans le temps exclusif d’application total de cette fonction.|  
|**Temps exclusif d’application moy.**|Temps exclusif d’application moyen d’un appel à cette fonction.|  
|**Temps exclusif d’application max.**|Temps exclusif d’application maximal d’un appel à cette fonction.|  
|**Temps exclusif d’application min.**|Temps exclusif d’application minimal d’un appel à cette fonction.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour personnaliser les colonnes de la vue Rapport](../profiling/how-to-customize-report-view-columns.md)   
 [Vue Fonctions](../profiling/functions-view-sampling-data.md)   
 [Vue Fonctions - Échantillonnage](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Vue Fonctions - Instrumentation](../profiling/functions-view-dotnet-memory-instrumentation-data.md)



