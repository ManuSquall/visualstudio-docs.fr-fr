---
title: "Mode Appelant/Appel&#233; - donn&#233;es d&#39;instrumentation de la m&#233;moire .NET du profileur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mode Appelant/Appelé"
ms.assetid: da624c06-8741-4afb-aad1-f8c0002f3de2
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Mode Appelant/Appel&#233; - donn&#233;es d&#39;instrumentation de la m&#233;moire .NET du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le mode Appelant\/Appelé des données de profilage de mémoire .NET collectées avec la méthode d'instrumentation affiche les données d'allocation et de temporisation d'une fonction sélectionnée, ainsi que les fonctions parents et enfants de cette fonction.  Le mode Appelant\/Appelé contient trois grilles.  
  
 La **Fonction active** s'affiche dans la grille centrale et contient les informations de profilage de mémoire sur la fonction sélectionnée.  Les valeurs comprennent tous les appels échantillonnés à la fonction.  
  
 **Fonctions qui ont appelé la fonction active** est affiché dans la grille supérieure et indique la quantité de valeur de la fonction sélectionnée \(active\) générée par les appels de la fonction d'appelant \(parent\).  
  
 **Fonctions qui ont été appelées par la fonction active** est affiché dans la grille inférieure et indique les données de profilage de mémoire des fonctions d'appelé \(enfant\) de la fonction sélectionnée lorsque la fonction enfant a été appelée par la fonction active.  
  
 Double\-cliquez sur une ligne de fonction appelant ou appelé pour transformer cette ligne en fonction active.  
  
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
|**ID de processus**|ID de processus de l'exécution du profilage.|  
|**Nom du processus**|Nom assigné au processus.|  
|**Temps exclusif de charge de la sonde**|Surcharge de temps pour cette fonction provoquée par l'instrumentation.  Le traitement de sondes a été soustrait de tous les temps exclusifs.|  
|**Temps inclusif de charge de la sonde**|Surcharge de temps pour cette fonction et ses fonctions enfants provoquée par l'instrumentation.  Le traitement de sondes a été soustrait de tous les temps inclusifs.|  
|**Type**|Contexte de la fonction :<br /><br /> **0** \- la fonction active<br /><br /> **1** \- une fonction qui appelle la fonction active<br /><br /> **2** \- une fonction qui est appelée par la fonction active<br /><br /> Uniquement dans les rapports en ligne de commande de [VSPerfReport](../profiling/vsperfreport.md).|  
|**Nom de la fonction racine**|Nom de la fonction actuelle.  Uniquement dans les rapports en ligne de commande de [VSPerfReport](../profiling/vsperfreport.md).|  
  
## Valeurs d'allocation de mémoire .NET  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Allocations exclusives**|-   Pour la fonction active, nombre d'objets créés lorsque la fonction exécutait du code dans le corps de la fonction, c'est\-à\-dire lorsque la fonction se situait en haut de la pile des appels.  Ce nombre ne comprend pas les objets créés dans les fonctions appelées par cette fonction.<br />-   Pour une fonction d'appelant, nombre d'allocations exclusives de la fonction active générées par les appels de cette fonction d'appelant.<br />-   Pour une fonction d'appelé, nombre d'objets créés par les instances de cette fonction appelés par la fonction active.  Ce nombre ne comprend pas les objets créés par les fonctions appelées par la fonction d'appelé.|  
|**Allocations exclusives %**|Pourcentage de tous les objets créés dans l'exécution du profilage qui correspondaient à des allocations exclusives de cette fonction.|  
|**Allocations inclusives**|-   Pour la fonction active, nombre d'objets alloués par la fonction dans l'exécution du profilage.  Ce nombre comprend les objets créés dans les fonctions d'appelé appelées par la fonction.<br />-   Pour une fonction d'appelant, nombre d'allocations inclusives de la fonction active générées par les appels de cette fonction d'appelant.<br />-   Pour une fonction d'appelé, nombre d'objets alloués par les instances de cette fonction qui ont été générés par les appels de la fonction active.  Le nombre inclut les allocations faites par les fonctions appelées par cette fonction d'appelé.|  
|**Allocations inclusives %**|Pourcentage de tous les objets créés dans l'exécution du profilage qui correspondaient à des allocations inclusives de cette fonction.|  
|**Octets exclusifs**|-   Pour la fonction actuelle, nombre d'octets de mémoire alloués par la fonction dans l'exécution du profilage.  Ce nombre ne comprend pas la mémoire qui a été allouée dans les fonctions d'appelé appelées par la fonction.<br />-   Pour une fonction d'appelant, nombre d'octets exclusifs de la fonction active générés par les appels de cette fonction d'appelant.<br />-   Pour une fonction d'appelé, nombre d'octets alloués par les instances de cette fonction qui ont été générées par des appels de la fonction active.  Ce nombre ne comprend pas les octets alloués par les fonctions appelées par la fonction d'appelé.|  
|**Octets exclusifs %**|Pourcentage de tous les octets de mémoire alloués dans l'exécution du profilage qui correspondaient à des allocations exclusives de cette fonction.|  
|**Octets inclusifs**|-   Pour la fonction active, nombre d'octets de mémoire alloués par la fonction dans l'exécution du profilage.  Ce nombre comprend la mémoire qui a été allouée dans les fonctions d'appelé appelées par la fonction.<br />-   Pour une fonction d'appelant, nombre d'octets inclusifs des instances de la fonction active générés par les appels de cette fonction d'appelant.<br />-   Pour une fonction d'appelé, nombre d'octets alloués par les instances de cette fonction qui ont été générées par des appels de la fonction active.  Ce nombre comprend les octets alloués par les fonctions appelées par cette fonction d'appelé.|  
|**Octets inclusifs %**|Pourcentage de tous les octets de mémoire alloués dans l'exécution du profilage qui correspondaient à des allocations inclusives de cette fonction.|  
  
## Valeurs inclusives écoulées  
 Les valeurs inclusives écoulées indiquent la durée pendant laquelle une fonction se trouvait sur la pile des appels.  La durée inclut le temps consacré aux fonctions enfant et aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps inclusif écoulé**|-   Pour la fonction active, temps consacré à la fonction.  La valeur inclut le temps consacré aux fonctions enfant et aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.<br />-   Pour une fonction d'appelant, fraction du temps inclusif écoulé de la fonction active générée par les appels de cette fonction d'appelant.<br />-   Pour une fonction d'appelé, temps passé dans cette fonction qui a été générée par des appels de la fonction actuelle.  La valeur inclut le temps consacré aux fonctions enfant et aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.|  
|**Temps inclusif écoulé en %**|Pourcentage du temps inclusif écoulé total dans l'exécution du profilage correspondant au temps inclusif écoulé de cette fonction dans ce contexte.|  
|**Temps inclusif écoulé moy.**|Temps inclusif écoulé moyen d'un appel à cette fonction dans ce contexte.|  
|**Temps inclusif écoulé max.**|Temps inclusif écoulé maximal d'un appel à cette fonction dans ce contexte.|  
|**Temps inclusif écoulé min.**|Temps inclusif écoulé minimal d'un appel à cette fonction dans ce contexte.|  
  
## Valeurs exclusives écoulées  
 Les valeurs exclusives écoulées indiquent la durée pendant laquelle une fonction s'exécutait directement en haut de la pile des appels.  Cette durée inclut le temps consacré aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie, mais elle n'inclut pas le temps passé dans les fonctions enfants.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps exclusif écoulé**|-   Pour la fonction active, temps consacré à l'exécution du corps de la fonction.  La valeur exclut le temps passé dans les fonctions enfants, mais inclut les appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.<br />-   Pour une fonction d'appelant, fraction du temps exclusif écoulé de la fonction active générée par les appels de cette fonction d'appelant.<br />-   Pour une fonction d'appelé, temps passé dans cette fonction qui a été générée par des appels de la fonction actuelle.  La valeur exclut le temps passé dans les fonctions enfants de la fonction d'appelant, mais inclut les appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.|  
|**Temps exclusif écoulé en %**|Pourcentage du temps exclusif écoulé total dans l'exécution du profilage dans le temps exclusif écoulé total de cette fonction dans ce contexte.|  
|**Temps exclusif écoulé moy.**|Temps exclusif écoulé moyen d'un appel à cette fonction dans ce contexte.|  
|**Temps exclusif écoulé max.**|Temps exclusif écoulé maximal d'un appel à cette fonction dans ce contexte.|  
|**Temps exclusif écoulé min.**|Temps exclusif écoulé minimal d'un appel à cette fonction dans ce contexte.|  
  
## Valeurs inclusives d'application  
 Les valeurs inclusives d'application indiquent la durée pendant laquelle une fonction se trouvait sur la pile des appels.  La durée n'inclut pas le temps consacré aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie, mais elle inclut le temps consacré aux fonctions enfants.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps inclusif d'application**|-   Pour la fonction active, temps consacré à la fonction et à ses fonctions enfants.  La valeur exclut le temps consacré aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.<br />-   Pour une fonction d'appelant, fraction du temps inclusif d'application de la fonction active générée par les appels de cette fonction d'appelant.<br />-   Pour une fonction d'appelé, temps passé dans cette fonction et ses fonctions enfants généré par les appels de la fonction active.  La valeur ne comprend pas le temps passé dans les appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.|  
|**Temps inclusif d'application en %**|Pourcentage du temps inclusif écoulé total dans l'exécution du profilage dans le temps inclusif d'application total de cette fonction dans ce contexte.|  
|**Temps inclusif d'application moy.**|Temps inclusif d'application moyen d'un appel à cette fonction dans ce contexte.|  
|**Temps inclusif d'application max.**|Temps inclusif d'application maximal d'un appel à cette fonction dans ce contexte.|  
|**Temps inclusif d'application min.**|Temps inclusif d'application minimal d'un appel à cette fonction dans ce contexte.|  
  
## Valeurs exclusives d'application  
 Les valeurs exclusives d'application indiquent le temps passé dans la fonction, à l'exclusion du temps passé dans les fonctions enfants.  Le temps indiqué exclut également le temps passé dans les appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps exclusif d'application**|-   Pour la fonction active, temps consacré à l'exécution du corps de la fonction.  Cette valeur n'inclut pas le temps passé dans les fonctions enfants, ni les appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.<br />-   Pour une fonction d'appelant, fraction du temps exclusif d'application de la fonction active généré par les appels de cette fonction d'appelant.<br />-   Pour une fonction d'appelé, temps passé dans cette fonction qui a été générée par des appels de la fonction actuelle.  La valeur n'inclut pas le temps passé dans les fonctions enfants de la fonction d'appelant, ni les appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.|  
|**Temps exclusif d'application en %**|Pourcentage du temps exclusif écoulé total dans l'exécution du profilage dans le temps exclusif d'application total de cette fonction dans ce contexte.|  
|**Temps exclusif d'application moy.**|Temps exclusif d'application moyen d'un appel à cette fonction dans ce contexte.|  
|**Temps exclusif d'application max.**|Temps exclusif d'application maximal d'un appel à cette fonction dans ce contexte.|  
|**Temps exclusif d'application min.**|Temps exclusif d'application minimal d'un appel à cette fonction dans ce contexte.|  
  
## Voir aussi  
 [Comment : personnaliser les colonnes de la vue de rapport](../profiling/how-to-customize-report-view-columns.md)   
 [Mode Appelant\/Appelé \- échantillonnage](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Mode Appelant\/Appelé](../profiling/caller-callee-view-instrumentation-data.md)   
 [Mode Appelant\/Appelé](../profiling/caller-callee-view-sampling-data.md)