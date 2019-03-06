---
title: Vue Fonctions - Données d’instrumentation de la mémoire .NET | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: cd45b379-394b-4b71-828c-92cd89e46ae0
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 340a12bfb8dc9a26c4200682851bb0acc684dddf
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54787390"
---
# <a name="functions-view---net-memory-instrumentation-data"></a>Vue Fonctions - Données d’instrumentation de la mémoire .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La vue Fonctions des données de profilage de l’allocation mémoire de .NET qui ont été collectées avec la méthode d’instrumentation liste les fonctions qui ont alloué de la mémoire lors de l’exécution du profilage. Une ligne de fonction indique la taille et le nombre d’allocations, ainsi que les données chronologiques de la fonction.  
  
## <a name="general"></a>Général  
  
|Colonne|Description|  
|------------|-----------------|  
|**Nom de la fonction**|Nom de la fonction.|  
|**Adresse de la fonction**|Adresse de la fonction.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Nombre d’appels**|Nombre total d'appels passés à cette fonction.|  
|**Fichier source**|Fichier source contenant la définition de cette fonction.|  
|**Nom du module**|Nom du module qui contient la fonction.|  
|**Chemin de module**|Chemin d’accès du module qui contient la fonction.|  
|**ID du processus**|ID du processus (PID) de l'exécution du profilage.|  
|**Nom du processus**|Nom du processus.|  
|**Traitement de sondes du temps exclusif**|Surcharge de temps pour cette fonction qui est provoquée par l’instrumentation. Le traitement de sondes a été soustrait de tous les temps exclusifs.|  
|**Traitement des sondes temps inclus**|Surcharge de temps pour cette fonction et ses fonctions enfants qui est provoquée par l’instrumentation. Le traitement de sondes a été soustrait de tous les temps inclusifs.|  
  
## <a name="net-memory-values"></a>Valeurs de mémoire .NET  
 Les valeurs de mémoire .NET inclusives d’une fonction indiquent le nombre (allocations) et la taille (octets) des objets créés par la fonction et ses fonctions enfants.  
  
 Les valeurs de mémoire exclusives indiquent le nombre et la taille des objets créés par la fonction, et non par ses fonctions enfants.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Allocations inclusives**|Nombre total d’objets créés dans cette fonction et dans les fonctions appelées par cette fonction.|  
|**% d’allocations inclusives**|Pourcentage de tous les objets alloués lors de l’exécution du profilage qui étaient des allocations inclusives de cette fonction.|  
|**Allocations exclusives**|Nombre total d’objets qui ont été créés quand la fonction exécutait du code du corps de la fonction. Ce nombre n’inclut pas les objets créés dans les fonctions appelées par cette fonction.|  
|**% d’allocations exclusives**|Pourcentage de tous les objets créés lors de l’exécution du profilage qui étaient des allocations exclusives de cette fonction.|  
|**Octets inclusifs**|Nombre d’octets de mémoire alloués dans cette fonction et dans les fonctions appelées par cette fonction.|  
|**% d’octets inclusifs**|Pourcentage de tous les octets de mémoire alloués lors de l’exécution du profilage, qui étaient des octets inclusifs de cette fonction.|  
|**Octets exclusifs**|Nombre d’octets de mémoire alloués dans cette fonction, mais pas dans les fonctions appelées par cette fonction.|  
|**% d’octets exclusifs**|Pourcentage de tous les octets de mémoire alloués lors de l’exécution du profilage, qui étaient des octets exclusifs de cette fonction.|  
  
## <a name="elapsed-inclusive-values"></a>Valeurs de temps inclusif écoulé  
 Les valeurs de temps inclusif écoulé indiquent le temps qu’a passé une fonction dans la pile des appels. Cette durée comprend le temps passé dans les fonctions enfants, ainsi que le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps inclusif écoulé**|Temps inclusif écoulé total de tous les appels à cette fonction.|  
|**% de temps inclusif écoulé**|Pourcentage du temps inclusif écoulé total de l’exécution de profilage passé dans le temps inclusif écoulé de cette fonction.|  
|**Temps inclusif écoulé moy.**|Temps inclusif écoulé moyen d’un appel à cette fonction.|  
|**Temps inclusif écoulé max.**|Temps inclusif écoulé maximal d’un appel à cette fonction.|  
|**Temps inclusif écoulé min.**|Temps inclusif écoulé minimal d’un appel à cette fonction.|  
  
## <a name="elapsed-exclusive-values"></a>Valeurs de temps exclusif écoulé  
 Les valeurs de temps exclusif écoulé indiquent la durée pendant laquelle une fonction s’est exécutée directement en haut de la pile des appels. Cette durée inclut le temps consacré aux appels émis vers le système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S, mais elle n’inclut pas le temps passé dans les fonctions enfants.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps exclusif écoulé**|Temps exclusif écoulé total de tous les appels à cette fonction.|  
|**% de temps exclusif écoulé**|Pourcentage du temps exclusif écoulé total de l’exécution de profilage passé dans le temps exclusif écoulé total de cette fonction.|  
|**Temps exclusif écoulé moy.**|Temps exclusif écoulé moyen d’un appel à cette fonction.|  
|**Temps exclusif écoulé max.**|Temps exclusif écoulé maximal d’un appel à cette fonction.|  
|**Temps exclusif écoulé min.**|Temps exclusif écoulé minimal d’un appel à cette fonction.|  
  
## <a name="application-inclusive-values"></a>Valeurs de temps inclusif d’application  
 Les valeurs de temps inclusif d’application indiquent le temps qu’a passé une fonction dans la pile des appels. Cette durée n’inclut pas le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S, mais elle inclut le temps passé dans les fonctions enfants.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps inclusif d’application**|Temps inclusif d’application total de tous les appels à cette fonction.|  
|**% du temps inclusif d’application**|Pourcentage du temps inclusif écoulé total de l’exécution de profilage passé dans le temps inclusif d’application total de cette fonction.|  
|**Temps inclusif d’application moy.**|Temps inclusif d’application moyen d’un appel à cette fonction.|  
|**Temps inclusif d’application max.**|Temps inclusif d’application maximal d’un appel à cette fonction.|  
|**Temps inclusif d’application min.**|Temps inclusif d’application minimal d’un appel à cette fonction.|  
  
## <a name="application-exclusive-values"></a>Valeurs de temps exclusif d’application  
 Les valeurs de temps exclusif d’application indiquent la durée pendant laquelle une fonction s’est exécutée directement en haut de la pile des appels. Cette durée n’inclut pas le temps passé dans les appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S, ni le temps passé dans les fonctions enfants.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps exclusif d’application**|Temps exclusif d’application total de tous les appels à cette fonction.|  
|**% du temps exclusif d’application**|Pourcentage du temps exclusif écoulé total de l’exécution de profilage passé dans le temps exclusif d’application total de cette fonction.|  
|**Temps exclusif d’application moy.**|Temps exclusif d’application moyen d’un appel à cette fonction.|  
|**Temps exclusif d’application max.**|Temps exclusif d’application maximal d’un appel à cette fonction.|  
|**Temps exclusif d’application min.**|Temps exclusif d’application minimal d’un appel à cette fonction.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour personnaliser les colonnes de la vue Rapport](../profiling/how-to-customize-report-view-columns.md)   
 [Vue Fonctions - Échantillonnage](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Mode Fonction](../profiling/functions-view-instrumentation-data.md)   
 [Mode Fonctions](../profiling/functions-view-sampling-data.md)
