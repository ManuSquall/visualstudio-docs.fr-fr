---
title: Vue Arborescence des appels - Données d’instrumentation | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Call Tree view
ms.assetid: 306bd176-0ce9-4a10-89ca-20b043d37d4e
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 630f75468adf5995eb887ac5f73d82462bfe32a4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786241"
---
# <a name="call-tree-view---instrumentation-data"></a>Vue Arborescence des appels - Données d’instrumentation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les valeurs d’une fonction dans l’arborescence des appels indiquent une durée pour les instances de fonctions qui ont été appelées par la fonction parent dans l’arborescence des appels. Les valeurs en pourcentage sont calculées en comparant la valeur des instances de fonctions au temps inclusif écoulé total de toutes les fonctions comprises dans l’exécution du profilage.  
  
## <a name="general"></a>Général  
 Les colonnes générales permettent d’identifier la fonction dans une ligne de la vue.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Nom de la fonction**|Nom de la fonction.|  
|**Adresse de la fonction**|Adresse de la fonction.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Nombre d’appels**|Nombre total d’appels passés à cette fonction.|  
|**Fichier source**|Fichier source contenant la définition pour cette fonction.|  
|**Nom du module**|Nom du module qui contient la fonction.|  
|**Chemin de module**|Chemin d’accès du module qui contient la fonction.|  
|**ID du processus**|ID du processus (PID) de l'exécution du profilage.|  
|**Nom du processus**|Nom assigné au processus.|  
|**Traitement de sondes du temps exclusif**|Surcharge de temps pour cette fonction qui est provoquée par l’instrumentation. Le traitement de sondes a été soustrait de tous les temps exclusifs.|  
|**Traitement des sondes temps inclus**|Surcharge de temps pour cette fonction et ses fonctions enfants qui est provoquée par l’instrumentation. Le traitement de sondes a été soustrait de tous les temps inclusifs.|  
|**Niveau**|Profondeur de la fonction dans l’arborescence des appels. Uniquement dans les rapports en ligne de commande [VSPerfReport](../profiling/vsperfreport.md).|  
  
## <a name="elapsed-inclusive-values"></a>Valeurs de temps inclusif écoulé  
 Les valeurs de temps inclusif écoulé indiquent une durée dans l’arborescence des appels des instances de fonctions qui ont été appelées par la fonction parent dans l’arborescence des appels. Cette durée comprend le temps passé dans les fonctions enfants qui ont été appelées par la fonction, ainsi que les appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps inclusif écoulé**|Temps inclusif écoulé total de tous les appels à cette fonction dans ce contexte.|  
|**% de temps inclusif écoulé**|Pourcentage du temps inclusif écoulé total de l’exécution de profilage passé dans le temps inclusif écoulé total de cette fonction dans ce contexte.|  
|**Temps inclusif écoulé moy.**|Temps inclusif écoulé moyen d’un appel à cette fonction dans ce contexte.|  
|**Temps inclusif écoulé max.**|Temps inclusif écoulé maximal d’un appel à cette fonction dans ce contexte.|  
|**Temps inclusif écoulé min.**|Temps inclusif écoulé minimal d’un appel à cette fonction dans ce contexte.|  
  
## <a name="elapsed-exclusive-values"></a>Valeurs de temps exclusif écoulé  
 Les valeurs de temps exclusif écoulé indiquent la durée pendant laquelle les instances d’une fonction, qui ont été appelées par la fonction parent dans l’arborescence des appels, ont exécuté du code dans le corps de la fonction, autrement dit, lorsque la fonction se trouvait en haut de la pile des appels. Cette durée inclut le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S. Toutefois, cette durée n’inclut pas le temps passé dans les fonctions enfants qui ont été appelées par la fonction.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps exclusif écoulé**|Temps exclusif écoulé total de tous les appels à cette fonction dans ce contexte.|  
|**% de temps exclusif écoulé**|Pourcentage du temps exclusif écoulé total de l’exécution de profilage passé dans le temps exclusif écoulé total de cette fonction dans ce contexte.|  
|**Temps exclusif écoulé moy.**|Temps exclusif écoulé moyen d’un appel à cette fonction dans ce contexte.|  
|**Temps exclusif écoulé max.**|Temps exclusif écoulé maximal d’un appel à cette fonction dans ce contexte.|  
|**Temps exclusif écoulé min.**|Temps exclusif écoulé minimal d’un appel à cette fonction dans ce contexte.|  
  
## <a name="application-inclusive-values"></a>Valeurs de temps inclusif d’application  
 Les valeurs de temps inclusif d’application indiquent la durée pendant laquelle les instances d’une fonction, qui ont été appelées par la fonction parent dans l’arborescence des appels, sont restées dans la pile des appels. Cette durée n’inclut pas le temps consacré aux appels passés au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S. Cependant, elle inclut le temps passé dans les fonctions enfants qui ont été appelées par la fonction.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps inclusif d’application**|Temps inclusif d’application total de tous les appels à cette fonction dans ce contexte.|  
|**% du temps inclusif d’application**|Pourcentage du temps inclusif écoulé total de l’exécution de profilage passé dans le temps inclusif d’application total de cette fonction dans ce contexte.|  
|**Temps inclusif d’application moy.**|Temps inclusif d’application moyen d’un appel à cette fonction dans ce contexte.|  
|**Temps inclusif d’application max.**|Temps inclusif d’application maximal d’un appel à cette fonction dans ce contexte.|  
|**Temps inclusif d’application min.**|Temps inclusif d’application minimal d’un appel à cette fonction dans ce contexte.|  
  
## <a name="application-exclusive-values"></a>Valeurs de temps exclusif d’application  
 Les valeurs de temps exclusif d’application indiquent la durée pendant laquelle les instances d’une fonction, qui ont été appelées par la fonction parent dans l’arborescence des appels, ont exécuté du code directement dans le corps de la fonction, autrement dit, lorsque la fonction se trouvait en haut de la pile des appels. Cette durée n’inclut pas le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S. Cette durée n’inclut pas non plus le temps passé dans les fonctions enfants qui ont été appelées par la fonction.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps exclusif d’application**|Temps exclusif d’application total de tous les appels à cette fonction dans ce contexte.|  
|**% du temps exclusif d’application**|Pourcentage du temps exclusif écoulé total de l’exécution de profilage passé dans le temps exclusif d’application total de cette fonction dans ce contexte.|  
|**Temps exclusif d’application moy.**|Temps exclusif d’application moyen d’un appel à cette fonction dans ce contexte.|  
|**Temps exclusif d’application max.**|Temps exclusif d’application maximal d’un appel à cette fonction dans ce contexte.|  
|**Temps exclusif d’application min.**|Temps exclusif d’application minimal d’un appel à cette fonction dans ce contexte.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour personnaliser les colonnes de la vue de rapport](../profiling/how-to-customize-report-view-columns.md)   
 [Vue Arborescence des appels](../profiling/call-tree-view-sampling-data.md)   
 [Vue Arborescence des appels - Instrumentation](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Vue Arborescence des appels - Échantillonnage](../profiling/call-tree-view-dotnet-memory-sampling-data.md)



