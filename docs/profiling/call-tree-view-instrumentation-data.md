---
title: "Mode Arborescence des appels - donn&#233;es d&#39;instrumentation du profileur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mode Arborescence des appels"
ms.assetid: 306bd176-0ce9-4a10-89ca-20b043d37d4e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Mode Arborescence des appels - donn&#233;es d&#39;instrumentation du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les valeurs pour une fonction dans l'arborescence des appels indiquent la période pour les instances de fonction qui ont été appelées par la fonction parente dans l'arborescence des appels.  Les valeurs en pourcentage sont calculées en comparant la valeur des instances de fonction et le temps inclusif écoulé total de toutes les fonctions dans l'exécution du profilage.  
  
## Général  
 Les colonnes générales identifient la fonction dans une ligne d'affichage.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Nom de la fonction**|Nom de la fonction.|  
|**Adresse de la fonction**|Adresse de la fonction.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Nombre d'appels**|Nombre total d'appels passés à cette fonction.|  
|**Source File**|Fichier source qui contient la définition de cette fonction.|  
|**Nom de module**|Nom du module qui contient la fonction.|  
|**Chemin de module**|Chemin d'accès du module qui contient la fonction.|  
|**ID de processus**|ID du processus \(PID\) de l'exécution du profilage.|  
|**Nom du processus**|Nom assigné au processus.|  
|**Temps exclusif de charge de la sonde**|Surcharge de temps pour cette fonction provoquée par l'instrumentation.  Le traitement de sondes a été soustrait de tous les temps exclusifs.|  
|**Temps inclusif de charge de la sonde**|Surcharge de temps pour cette fonction et ses fonctions enfants provoquée par l'instrumentation.  Le traitement de sondes a été soustrait de tous les temps inclusifs.|  
|**Niveau**|Profondeur de la fonction dans l'arborescence des appels.  Uniquement dans les rapports en ligne de commande de [VSPerfReport](../profiling/vsperfreport.md).|  
  
## Valeurs inclusives écoulées  
 Les valeurs inclusives écoulées indiquent le temps sur la pile des appels de ces instances de la fonction qui ont été appelées par la fonction parente dans l'arborescence des appels.  Cette durée inclut le temps consacré aux fonctions enfants appelées par la fonction et au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps inclusif écoulé**|Temps inclusif écoulé total de tous les appels à cette fonction dans ce contexte.|  
|**Temps inclusif écoulé en %**|Pourcentage du temps inclusif écoulé total dans l'exécution du profilage consacré au temps inclusif écoulé total de cette fonction dans ce contexte.|  
|**Temps inclusif écoulé moy.**|Temps inclusif écoulé moyen d'un appel à cette fonction dans ce contexte.|  
|**Temps inclusif écoulé max.**|Temps inclusif écoulé maximal d'un appel à cette fonction dans ce contexte.|  
|**Temps inclusif écoulé min.**|Temps inclusif écoulé minimal d'un appel à cette fonction dans ce contexte.|  
  
## Valeurs exclusives écoulées  
 Les valeurs exclusives écoulées indiquent la durée pendant laquelle ces instances d'une fonction appelées par la fonction parente dans l'arborescence des appels exécutaient le code dans le corps de la fonction, c'est\-à\-dire lorsque la fonction était en haut de la pile des appels.  Le temps comprend le temps passé dans les appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.  Cependant, le temps n'inclut pas le temps passé dans les fonctions enfants appelées par la fonction.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps exclusif écoulé**|Temps exclusif écoulé total de tous les appels à cette fonction dans ce contexte.|  
|**Temps exclusif écoulé en %**|Pourcentage du temps exclusif écoulé total dans l'exécution du profilage dans le temps exclusif écoulé total de cette fonction dans ce contexte.|  
|**Temps exclusif écoulé moy.**|Temps exclusif écoulé moyen d'un appel à cette fonction dans ce contexte.|  
|**Temps exclusif écoulé max.**|Temps exclusif écoulé maximal d'un appel à cette fonction dans ce contexte.|  
|**Temps exclusif écoulé min.**|Temps exclusif écoulé minimal d'un appel à cette fonction dans ce contexte.|  
  
## Valeurs inclusives d'application  
 Les valeurs inclusives d'application indiquent le temps pendant lequel les instances d'une fonction appelées par la fonction parente dans l'arborescence des appels étaient sur la pile des appels.  La durée n'inclut pas le temps consacré aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie. Cependant, elle inclut le temps consacré aux fonctions enfants qui ont été appelées par la fonction.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps inclusif d'application**|Temps inclusif d'application total de tous les appels à cette fonction dans ce contexte.|  
|**Temps inclusif d'application en %**|Pourcentage du temps inclusif écoulé total dans l'exécution du profilage dans le temps inclusif d'application total de cette fonction dans ce contexte.|  
|**Temps inclusif d'application moy.**|Temps inclusif d'application moyen d'un appel à cette fonction dans ce contexte.|  
|**Temps inclusif d'application max.**|Temps inclusif d'application maximal d'un appel à cette fonction dans ce contexte.|  
|**Temps inclusif d'application min.**|Temps inclusif d'application minimal d'un appel à cette fonction dans ce contexte.|  
  
## Valeurs exclusives d'application  
 Les valeurs exclusives d'application indiquent la durée pendant laquelle ces instances d'une fonction appelées par la fonction parente dans l'arborescence des appels exécutaient directement le code dans le corps de la fonction, c'est\-à\-dire, lorsque la fonction était en haut de la pile des appels.  La durée ne comprend pas le temps passé dans les appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.  En outre, il n'inclut pas le temps passé dans les fonctions enfants appelées par la fonction.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps exclusif d'application**|Temps exclusif d'application total de tous les appels à cette fonction dans ce contexte.|  
|**Temps exclusif d'application en %**|Pourcentage du temps exclusif écoulé total dans l'exécution du profilage dans le temps exclusif d'application total de cette fonction dans ce contexte.|  
|**Temps exclusif d'application moy.**|Temps exclusif d'application moyen d'un appel à cette fonction dans ce contexte.|  
|**Temps exclusif d'application max.**|Temps exclusif d'application maximal d'un appel à cette fonction dans ce contexte.|  
|**Temps exclusif d'application min.**|Temps exclusif d'application minimal d'un appel à cette fonction dans ce contexte.|  
  
## Voir aussi  
 [Comment : personnaliser les colonnes de la vue de rapport](../profiling/how-to-customize-report-view-columns.md)   
 [Mode Arborescence des appels](../profiling/call-tree-view-sampling-data.md)   
 [Mode Arborescence des appels \- instrumentation](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Mode Arborescence des appels \- échantillonnage](../profiling/call-tree-view-dotnet-memory-sampling-data.md)