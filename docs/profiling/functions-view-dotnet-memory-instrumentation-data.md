---
title: "Mode Fonctions - donn&#233;es d&#39;instrumentation de la m&#233;moire .NET du profileur | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mode Fonctions"
ms.assetid: cd45b379-394b-4b71-828c-92cd89e46ae0
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Mode Fonctions - donn&#233;es d&#39;instrumentation de la m&#233;moire .NET du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le mode Fonctions des données de profilage d'allocation de mémoire .NET collectées à l'aide de la méthode d'instrumentation répertorie les fonctions qui ont alloué de la mémoire pendant l'exécution du profilage.  Une ligne de fonction consigne la taille et le nombre d'allocations, ainsi que les données de temporisation pour la fonction.  
  
## Général  
  
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
|**Nom du processus**|Nom du processus.|  
|**Temps exclusif de charge de la sonde**|Surcharge de temps pour cette fonction provoquée par l'instrumentation.  Le traitement de sondes a été soustrait de tous les temps exclusifs.|  
|**Temps inclusif de charge de la sonde**|Surcharge de temps pour cette fonction et ses fonctions enfants provoquée par l'instrumentation.  Le traitement de sondes a été soustrait de tous les temps inclusifs.|  
  
## Valeurs de mémoire .NET  
 Les valeurs de mémoire .NET inclusives d'une fonction indiquent le nombre \(allocations\) et la taille \(octets\) des objets créés par la fonction et ses fonctions enfants.  
  
 Les valeurs de mémoire exclusives indiquent le nombre et la taille des objets créés par la fonction et non pas par ses fonctions enfants.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Allocations inclusives**|Nombre total d'objets créé dans cette fonction et les fonctions appelées par cette fonction.|  
|**Allocations inclusives %**|Pourcentage de tous les objets alloués dans l'exécution du profilage qui correspondaient à des allocations inclusives de cette fonction.|  
|**Allocations exclusives**|Nombre total d'objets créés lorsque la fonction exécutait le code dans le corps de la fonction.  Ce nombre ne comprend pas les objets créés dans les fonctions appelées par cette fonction.|  
|**Allocations exclusives %**|Pourcentage de tous les objets créés dans l'exécution du profilage qui correspondaient à des allocations exclusives de cette fonction.|  
|**Octets inclusifs**|Nombre d'octets de mémoire alloués à cette fonction et aux fonctions appelées par cette fonction.|  
|**Octets inclusifs %**|Pourcentage de tous les octets de mémoire alloués dans l'exécution du profilage qui correspondaient à des octets inclusifs de cette fonction.|  
|**Octets exclusifs**|Nombre d'octets de mémoire alloués par cette fonction mais pas par les fonctions appelées par elle.|  
|**Octets exclusifs %**|Pourcentage de tous les octets de mémoire alloués dans l'exécution du profilage qui correspondaient à des octets exclusifs de cette fonction.|  
  
## Valeurs inclusives écoulées  
 Les valeurs inclusives écoulées indiquent la durée pendant laquelle une fonction se trouvait sur la pile des appels.  La durée inclut le temps consacré aux fonctions enfant et aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps inclusif écoulé**|Temps inclusif écoulé total correspondant à tous les appels à cette fonction.|  
|**Temps inclusif écoulé en %**|Pourcentage du temps inclusif écoulé total de l'exécution du profilage qui correspond au temps inclusif écoulé de cette fonction.|  
|**Temps inclusif écoulé moy.**|Temps inclusif écoulé moyen d'un appel à cette fonction.|  
|**Temps inclusif écoulé max.**|Temps inclusif écoulé maximal d'un appel à cette fonction.|  
|**Temps inclusif écoulé min.**|Temps inclusif écoulé minimal d'un appel à cette fonction.|  
  
## Valeurs exclusives écoulées  
 Les valeurs exclusives écoulées indiquent la durée pendant laquelle une fonction s'exécutait directement en haut de la pile des appels.  Cette durée inclut le temps consacré aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie, mais elle n'inclut pas le temps passé dans les fonctions enfants.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps exclusif écoulé**|Temps exclusif écoulé total correspondant à tous les appels à cette fonction.|  
|**Temps exclusif écoulé en %**|Pourcentage du temps exclusif écoulé total dans l'exécution du profilage correspondant au temps exclusif écoulé de cette fonction.|  
|**Temps exclusif écoulé moy.**|Temps exclusif écoulé moyen d'un appel à cette fonction.|  
|**Temps exclusif écoulé max.**|Temps exclusif écoulé maximal d'un appel à cette fonction.|  
|**Temps exclusif écoulé min.**|Temps exclusif écoulé minimal d'un appel à cette fonction.|  
  
## Valeurs inclusives d'application  
 Les valeurs inclusives d'application indiquent la durée pendant laquelle une fonction se trouvait sur la pile des appels.  La durée n'inclut pas le temps consacré aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie, mais elle inclut le temps consacré aux fonctions enfants.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps inclusif d'application**|Temps inclusif d'application total correspondant à tous les appels à cette fonction.|  
|**Temps inclusif d'application en %**|Pourcentage du temps inclusif écoulé total de l'exécution du profilage correspondant au temps inclusif d'application total de cette fonction.|  
|**Temps inclusif d'application moy.**|Temps inclusif d'application moyen d'un appel à cette fonction.|  
|**Temps inclusif d'application max.**|Temps inclusif d'application maximal d'un appel à cette fonction.|  
|**Temps inclusif d'application min.**|Temps inclusif d'application minimal d'un appel à cette fonction.|  
  
## Valeurs exclusives d'application  
 Les valeurs exclusives d'application indiquent la durée pendant laquelle une fonction s'exécutait directement en haut de la pile des appels.  La durée n'inclut pas le temps consacré aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie, pas plus que le temps passé dans les fonctions enfants.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps exclusif d'application**|Temps exclusif d'application total correspondant à tous les appels à cette fonction.|  
|**Temps exclusif d'application en %**|Pourcentage du temps exclusif écoulé total de l'exécution du profilage correspondant au temps exclusif d'application total de cette fonction.|  
|**Temps exclusif d'application moy.**|Temps exclusif d'application moyen d'un appel à cette fonction.|  
|**Temps exclusif d'application max.**|Temps exclusif d'application maximal d'un appel à cette fonction.|  
|**Temps exclusif d'application min.**|Temps exclusif d'application minimal d'un appel à cette fonction.|  
  
## Voir aussi  
 [Comment : personnaliser les colonnes de la vue de rapport](../profiling/how-to-customize-report-view-columns.md)   
 [Mode Fonctions \- échantillonnage](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Mode Fonction](../profiling/functions-view-instrumentation-data.md)   
 [Mode Fonctions](../profiling/functions-view-sampling-data.md)