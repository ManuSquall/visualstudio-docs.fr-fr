---
title: "Mode Appelant/Appel&#233; - donn&#233;es d&#39;instrumentation du profileur | Microsoft Docs"
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
ms.assetid: 0908d354-aa5c-4518-8631-e25b8e7649e5
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Mode Appelant/Appel&#233; - donn&#233;es d&#39;instrumentation du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le mode Appelant\/Appelé affiche les informations de profilage sur une fonction sélectionnée et ses fonctions parents et enfants dans l'arborescence des appels.  Le mode Appelant\/Appelé contient trois grilles.  
  
 La **Fonction active** s'affiche dans la grille centrale et contient les informations de profilage sur la fonction sélectionnée.  Les valeurs incluent tous les appels à la fonction.  
  
 Les **Fonctions qui ont appelé la fonction active** sont affichées dans la grille supérieure, et sont affichées également des informations de profilage sur les fonctions d'appelant \(parent\) de la fonction sélectionnée.  Les valeurs indiquent le montant de la valeur de la fonction active générée par les appels de cette fonction d'appelant.  
  
 Les **Fonctions qui ont été appelées par la fonction active** sont affichées dans la grille inférieure, et sont affichées également des informations de profilage sur les instances de fonctions d'appelant \(parent\) de la fonction sélectionnée.  Les valeurs indiquent uniquement le temps consacré à la fonction enfant appelée par la fonction active.  
  
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
|**Nom du processus**|Nom du processus.|  
|**Temps exclusif de charge de la sonde**|Surcharge de temps pour cette fonction provoquée par l'instrumentation.  Le traitement de sondes a été soustrait de tous les temps exclusifs.|  
|**Temps inclusif de charge de la sonde**|Surcharge de temps pour cette fonction et ses fonctions enfants provoquée par l'instrumentation.  Le traitement de sondes a été soustrait de tous les temps inclusifs.|  
|**Type**|Contexte de la fonction :<br /><br /> **0** \- la fonction active<br /><br /> **1** \- une fonction qui appelle la fonction active<br /><br /> **2** \- une fonction qui est appelée par la fonction active<br /><br /> Uniquement dans les rapports en ligne de commande de [VSPerfReport](../profiling/vsperfreport.md).|  
|**Nom de la fonction racine**|Nom de la fonction actuelle.  Uniquement dans les rapports en ligne de commande de [VSPerfReport](../profiling/vsperfreport.md).|  
  
## Valeurs inclusives écoulées  
 Les valeurs inclusives écoulées indiquent la durée pendant laquelle une fonction se trouvait sur la pile des appels.  La durée inclut le temps consacré aux fonctions enfants et le temps consacré aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps inclusif écoulé**|-   Pour la fonction active, temps consacré à la fonction.  La valeur inclut le temps consacré aux fonctions enfant et aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.<br />-   Pour une fonction d'appelant, fraction du temps inclusif écoulé de la fonction active générée par les appels de cette fonction d'appelant.<br />-   Pour une fonction d'appelé, temps passé dans les instances de cette fonction qui ont été générées par des appels de la fonction actuelle.  La valeur inclut le temps consacré aux fonctions enfants de l'appelant et aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.|  
|**Temps inclusif écoulé en %**|Pourcentage du temps inclusif écoulé total dans l'exécution du profilage correspondant au temps inclusif écoulé de cette fonction dans ce contexte.|  
|**Temps inclusif écoulé moy.**|Temps inclusif écoulé moyen d'un appel à cette fonction dans ce contexte.|  
|**Temps inclusif écoulé max.**|Temps inclusif écoulé maximal d'un appel à cette fonction dans ce contexte.|  
|**Temps inclusif écoulé min.**|Temps inclusif écoulé minimal d'un appel à cette fonction dans ce contexte.|  
  
## Valeurs exclusives écoulées  
 Les valeurs exclusives écoulées indiquent la durée pendant laquelle une fonction s'exécutait directement en haut de la pile des appels.  La durée inclut le temps consacré aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie, mais elle n'inclut pas le temps passé dans les fonctions enfants.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps exclusif écoulé**|-   Pour la fonction active, temps consacré à l'exécution directe de la fonction.  La valeur inclut le temps consacré aux fonctions enfant et aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.<br />-   Pour une fonction d'appelant, fraction du temps exclusif écoulé de la fonction active générée par les appels de cette fonction d'appelant.<br />-   Pour une fonction d'appelé, temps passé dans les instances de cette fonction qui ont été générées par des appels de la fonction actuelle.  La valeur exclut le temps consacré aux fonctions enfants de la fonction d'appelant, mais elle inclut les appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.|  
|**Temps exclusif écoulé en %**|Pourcentage du temps exclusif écoulé total dans l'exécution du profilage dans le temps exclusif écoulé total de cette fonction dans ce contexte.|  
|**Temps exclusif écoulé moy.**|Temps exclusif écoulé moyen d'un appel à cette fonction dans ce contexte.|  
|**Temps exclusif écoulé max.**|Temps exclusif écoulé maximal d'un appel à cette fonction dans ce contexte.|  
|**Temps exclusif écoulé min.**|Temps exclusif écoulé minimal d'un appel à cette fonction dans ce contexte.|  
  
## Valeurs inclusives d'application  
 Les valeurs inclusives d'application indiquent la durée pendant laquelle une fonction se trouvait sur la pile des appels.  La durée n'inclut pas le temps consacré aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie, mais elle inclut le temps consacré aux fonctions enfants.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps inclusif d'application**|-   Pour la fonction active, temps consacré à la fonction et à ses fonctions enfants.  La valeur exclut le temps consacré aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.<br />-   Pour une fonction d'appelant, fraction du temps inclusif d'application de la fonction active générée par les appels de cette fonction d'appelant.<br />-   Pour une fonction d'appelé, temps passé dans les instances de cette fonction qui ont été générées par des appels de la fonction actuelle.  La valeur inclut le temps consacré aux fonctions enfants de la fonction d'appelant, mais elle n'inclut pas le temps consacré aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.|  
|**Temps inclusif d'application en %**|Pourcentage du temps inclusif écoulé total dans l'exécution du profilage dans le temps inclusif d'application total de cette fonction dans ce contexte.|  
|**Temps inclusif d'application moy.**|Temps inclusif d'application moyen d'un appel à cette fonction dans ce contexte.|  
|**Temps inclusif d'application max.**|Temps inclusif d'application maximal d'un appel à cette fonction dans ce contexte.|  
|**Temps inclusif d'application min.**|Temps inclusif d'application minimal d'un appel à cette fonction dans ce contexte.|  
  
## Valeurs exclusives d'application  
 Les valeurs exclusives d'application indiquent le temps passé dans la fonction.  Cela exclut le temps consacré aux fonctions enfants et également le temps consacré aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps exclusif d'application**|-   Pour la fonction active, temps consacré à l'exécution directe de la fonction.  Cette valeur n'inclut pas le temps passé dans les fonctions enfants, ni les appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.<br />-   Pour une fonction d'appelant, fraction du temps exclusif d'application de la fonction active généré par les appels de cette fonction d'appelant.<br />-   Pour une fonction d'appelé, temps passé dans les instances de cette fonction qui ont été générées par des appels de la fonction actuelle.  La valeur n'inclut pas le temps passé dans les fonctions enfants de la fonction d'appelant, ni les appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.|  
|**Temps exclusif d'application en %**|Pourcentage du temps exclusif écoulé total dans l'exécution du profilage dans le temps exclusif d'application total de cette fonction dans ce contexte.|  
|**Temps exclusif d'application moy.**|Temps exclusif d'application moyen d'un appel à cette fonction dans ce contexte.|  
|**Temps exclusif d'application max.**|Temps exclusif d'application maximal d'un appel à cette fonction dans ce contexte.|  
|**Temps exclusif d'application min.**|Temps exclusif d'application minimal d'un appel à cette fonction dans ce contexte.|  
  
## Voir aussi  
 [Comment : personnaliser les colonnes de la vue de rapport](../profiling/how-to-customize-report-view-columns.md)   
 [Mode Appelant\/Appelé](../profiling/caller-callee-view-sampling-data.md)   
 [Mode Appelant\/Appelé \- échantillonnage](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Mode Appelant\/Appelé \- instrumentation](../profiling/caller-callee-view-net-memory-instrumentation-data.md)