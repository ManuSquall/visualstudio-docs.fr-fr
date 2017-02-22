---
title: "Vue Modules - donn&#233;es d&#39;instrumentation du profileur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Modules (vue)"
ms.assetid: 895b9589-1987-4160-916f-53b898a69cf0
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Vue Modules - donn&#233;es d&#39;instrumentation du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vue Modules affiche les données de performances groupées selon les modules contenus dans les données de profilage.  Les fonctions du module sont répertoriées sous le nœud de module.  
  
## Général  
 Les colonnes générales identifient la fonction dans une ligne d'affichage.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Name**|Nom de la fonction ou du module.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Nombre d'appels**|Nombre total d'appels faits à cette fonction ou ce module.|  
|**Source File**|Fichier source qui contient la définition de cette fonction.|  
|**Nom de module**|Nom du module qui contient la fonction.|  
|**Chemin de module**|Chemin d'accès du module qui contient la fonction.|  
|**ID de processus**|ID du processus \(PID\) de l'exécution du profilage.|  
|**Nom du processus**|Nom du processus dans lequel le module ou la fonction s'exécutait.|  
|**Temps exclusif de charge de la sonde**|Surcharge de temps pour cette fonction ou module en raison de l'instrumentation.|  
|**Temps inclusif de charge de la sonde**|Surcharge de temps pour cette fonction ou module et ses fonctions enfants en raison de l'instrumentation.|  
  
## Valeurs inclusives écoulées  
 Les valeurs inclusives écoulées indiquent la durée pendant laquelle une fonction se trouvait sur la pile des appels.  La durée inclut le temps consacré aux fonctions enfant et aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps inclusif écoulé**|-   Pour une fonction, temps consacré à la fonction.  Cela inclut le temps consacré aux fonctions enfant et aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.<br />-   Pour un module, la période pendant laquelle au moins une fonction dans le module se trouvait dans la pile des appels.|  
|**Temps inclusif écoulé en %**|Pourcentage du temps inclusif écoulé total de l'exécution du profilage consacré au temps inclusif écoulé de ce module ou cette fonction.|  
|**Temps inclusif écoulé moy.**|-   Pour une fonction, temps inclusif écoulé moyen d'un appel à cette fonction.<br />-   Pour un module, temps inclusif écoulé moyen de tous les appels aux fonctions dans le module.|  
|**Temps inclusif écoulé max.**|-   Pour une fonction, temps inclusif écoulé maximum d'un appel à cette fonction.<br />-   Pour un module, temps inclusif écoulé maximum de tous les appels aux fonctions dans le module.|  
|**Temps inclusif écoulé min.**|-   Pour une fonction, temps inclusif écoulé minimum d'un appel à ce module ou cette fonction.<br />-   Pour un module, temps inclusif écoulé minimum de tous les appels aux fonctions dans le module.|  
  
## Valeurs exclusives écoulées  
 Les valeurs exclusives écoulées indiquent la durée pendant laquelle une fonction s'exécutait directement en haut de la pile des appels.  La durée inclut le temps consacré aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie, mais elle n'inclut pas le temps passé dans les fonctions enfants.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps exclusif écoulé**|-   Pour une fonction, temps passé dans le module ou la fonction.  Cela inclut les appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie, mais exclut le temps passé dans les fonctions enfants.<br />-   Pour un module, somme des temps exclusifs écoulés des fonctions dans le module.|  
|**Temps exclusif écoulé en %**|Pourcentage du temps exclusif écoulé total de l'exécution du profilage consacré au temps exclusif écoulé de ce module ou cette fonction.|  
|**Temps exclusif écoulé moy.**|-   Pour une fonction, temps exclusif écoulé moyen d'un appel à cette fonction.<br />-   Pour un module, temps exclusif écoulé moyen de tous les appels aux fonctions dans le module.|  
|**Temps exclusif écoulé max.**|-   Pour une fonction, temps exclusif écoulé maximum d'un appel à cette fonction.<br />-   Pour un module, temps exclusif écoulé maximum de tous les appels aux fonctions dans le module.|  
|**Temps exclusif écoulé min.**|-   Pour une fonction, temps exclusif écoulé minimum d'un appel à ce module ou cette fonction.<br />-   Pour un module, temps exclusif écoulé minimum de tous les appels aux fonctions dans le module.|  
  
## Valeurs inclusives d'application  
 Les valeurs inclusives d'application indiquent la durée pendant laquelle une fonction se trouvait sur la pile des appels.  La durée n'inclut pas le temps consacré aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie. Cependant, elle inclut le temps passé dans les fonctions enfants.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps inclusif d'application**|-   Pour la fonction, temps consacré aux appels de la fonction.  Cela inclut le temps passé dans les fonctions enfants, mais exclut les appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.<br />-   Pour un module, la période pendant laquelle au moins une fonction dans le module se trouvait dans la pile des appels.  Cela exclut le temps passé dans les appels au système d'exploitation.|  
|**Temps inclusif d'application en %**|Pourcentage du temps inclusif écoulé total de l'exécution du profilage consacré au temps inclusif d'application de ce module ou cette fonction.|  
|**Temps inclusif d'application moy.**|-   Pour une fonction, temps inclusif d'application moyen d'un appel à cette fonction.<br />-   Pour un module, temps inclusif d'application moyen de tous les appels aux fonctions dans le module.|  
|**Temps inclusif d'application max.**|-   Pour une fonction, temps inclusif d'application maximum d'un appel à cette fonction.<br />-   Pour un module, temps inclusif d'application maximum de tous les appels aux fonctions dans le module.|  
|**Temps inclusif d'application min.**|-   Pour une fonction, temps inclusif d'application minimum d'un appel à ce module ou cette fonction.<br />-   Pour un module, temps inclusif d'application minimum de tous les appels aux fonctions dans le module.|  
  
## Valeurs exclusives d'application  
 Les valeurs exclusives d'application indiquent le temps passé dans le module ou la fonction.  Cela exclut le temps consacré aux fonctions enfants et également le temps consacré aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps exclusif d'application**|Temps exclusif d'application total de tous les appels à ce module ou cette fonction.|  
|**Temps exclusif d'application en %**|Pourcentage du temps exclusif écoulé total de l'exécution du profilage consacré au temps exclusif d'application de ce module ou cette fonction.|  
|**Temps exclusif d'application moy.**|-   Pour une fonction, temps exclusif d'application moyen d'un appel à cette fonction.<br />-   Pour un module, temps exclusif d'application moyen de tous les appels aux fonctions dans le module.|  
|**Temps exclusif d'application max.**|-   Pour une fonction, temps exclusif d'application maximum d'un appel à cette fonction.<br />-   Pour un module, temps exclusif d'application maximum de tous les appels aux fonctions dans le module.|  
|**Temps exclusif d'application min.**|-   Pour une fonction, temps exclusif d'application minimum d'un appel à ce module ou cette fonction.<br />-   Pour un module, temps exclusif d'application minimum de tous les appels aux fonctions dans le module.|  
  
## Voir aussi  
 [Modules, mode](../profiling/modules-view-sampling-data.md)   
 [Vue Modules \- instrumentation](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Vue Modules \- échantillonnage](../profiling/modules-view-dotnet-memory-sampling-data.md)