---
title: "Vue Appelant/Appelé - Données d’instrumentation | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Caller/Callee view
ms.assetid: 0908d354-aa5c-4518-8631-e25b8e7649e5
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5dafa487a8f81248250f8e1fd0d6c52e90982f76
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="callercallee-view---instrumentation-data"></a>Vue Appelant/Appelé - Données d’instrumentation
La vue Appelant/Appelé affiche des données de profilage pour la fonction sélectionnée, ainsi que pour ses fonctions parents et enfants dans l’arborescence des appels. La vue Appelant/Appelé comprend trois grilles.  
  
 La grille centrale intitulée **Fonction active** contient les informations de profilage associées à la fonction sélectionnée. Les valeurs incluent tous les appels à la fonction.  
  
 La grille supérieure intitulée **Fonctions qui ont appelé la fonction active** contient des informations de profilage concernant les fonctions d’appelant (parents) de la fonction sélectionnée. Ces informations indiquent la valeur de la fonction active qui a été générée par les appels de cette fonction d’appelant.  
  
 La grille inférieure intitulée **Fonctions qui ont été appelées par la fonction active** contient des informations de profilage concernant les instances des fonctions d’appelé (enfants) de la fonction sélectionnée. Ces valeurs indiquent uniquement le temps passé dans la fonction enfant quand celle-ci a été appelée par la fonction active.  
  
## <a name="general"></a>Général  
 Les colonnes générales permettent d’identifier la fonction dans une ligne de la vue.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Nom de la fonction**|Nom de la fonction.|  
|**Adresse de la fonction**|Adresse de la fonction.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Nombre d’appels**|Nombre total d’appels émis vers cette fonction.|  
|**Fichier source**|Fichier source contenant la définition pour cette fonction.|  
|**Nom du module**|Nom du module qui contient la fonction.|  
|**Chemin de module**|Chemin d’accès du module qui contient la fonction.|  
|**ID du processus**|ID du processus (PID) de l'exécution du profilage.|  
|**Nom du processus**|Nom du processus.|  
|**Traitement de sondes du temps exclusif**|Surcharge de temps pour cette fonction qui est provoquée par l’instrumentation. Le traitement de sondes a été soustrait de tous les temps exclusifs.|  
|**Traitement des sondes temps inclus**|Surcharge de temps pour cette fonction et ses fonctions enfants qui est provoquée par l’instrumentation. Le traitement de sondes a été soustrait de tous les temps inclusifs.|  
|**Type**|Contexte de la fonction :<br /><br /> **0** : la fonction active.<br /><br /> **1** : fonction qui appelle la fonction active<br /><br /> **2** : fonction qui est appelée par la fonction active<br /><br /> Uniquement dans les rapports en ligne de commande [VSPerfReport](../profiling/vsperfreport.md).|  
|**Nom de fonction racine**|Nom de la fonction active. Uniquement dans les rapports en ligne de commande [VSPerfReport](../profiling/vsperfreport.md).|  
  
## <a name="elapsed-inclusive-values"></a>Valeurs de temps inclusif écoulé  
 Les valeurs de temps inclusif écoulé indiquent le temps qu’a passé une fonction dans la pile des appels. Cette durée comprend le temps passé dans les fonctions enfants, ainsi que le temps consacré aux appels émis vers le système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps inclusif écoulé**|- Pour la fonction active, temps passé dans la fonction. Cette valeur comprend le temps passé dans les fonctions enfants, ainsi que le temps consacré aux appels émis vers le système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.<br />- Pour une fonction d’appelant, temps inclusif écoulé de la fonction active qui a été générée par les appels de cette fonction d’appelant.<br />- Pour une fonction d’appelé, temps passé dans les instances de cette fonction qui ont été générées par les appels émis par la fonction active. Cette valeur comprend le temps passé dans les fonctions enfants de l’appelé, ainsi que le temps consacré aux appels émis vers le système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.|  
|**% de temps inclusif écoulé**|Pourcentage du temps inclusif écoulé total de l’exécution de profilage passé dans le temps inclusif écoulé de cette fonction dans ce contexte.|  
|**Temps inclusif écoulé moy.**|Temps inclusif écoulé moyen d’un appel à cette fonction dans ce contexte.|  
|**Temps inclusif écoulé max.**|Temps inclusif écoulé maximal d’un appel à cette fonction dans ce contexte.|  
|**Temps inclusif écoulé min.**|Temps inclusif écoulé minimal d’un appel à cette fonction dans ce contexte.|  
  
## <a name="elapsed-exclusive-values"></a>Valeurs de temps exclusif écoulé  
 Les valeurs de temps exclusif écoulé indiquent la durée pendant laquelle une fonction s’est exécutée directement en haut de la pile des appels. Cette durée inclut le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S, mais elle n’inclut pas le temps passé dans les fonctions enfants.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps exclusif écoulé**|- Pour la fonction active, temps consacré à l’exécution directe de la fonction. Cette valeur comprend le temps passé dans les fonctions enfants, ainsi que le temps consacré aux appels émis vers le système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.<br />- Pour une fonction d’appelant, temps exclusif écoulé de la fonction active qui a été générée par les appels de cette fonction d’appelant.<br />- Pour une fonction d’appelé, temps passé dans les instances de cette fonction qui ont été générées par les appels émis par la fonction active. Cette valeur n’inclut pas le temps passé dans les fonctions enfants de la fonction d’appelé, mais elle inclut le temps consacré aux appels émis vers le système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.|  
|**% de temps exclusif écoulé**|Pourcentage du temps exclusif écoulé total de l’exécution de profilage passé dans le temps exclusif écoulé total de cette fonction dans ce contexte.|  
|**Temps exclusif écoulé moy.**|Temps exclusif écoulé moyen d’un appel à cette fonction dans ce contexte.|  
|**Temps exclusif écoulé max.**|Temps exclusif écoulé maximal d’un appel à cette fonction dans ce contexte.|  
|**Temps exclusif écoulé min.**|Temps exclusif écoulé minimal d’un appel à cette fonction dans ce contexte.|  
  
## <a name="application-inclusive-values"></a>Valeurs de temps inclusif d’application  
 Les valeurs de temps inclusif d’application indiquent le temps qu’a passé une fonction dans la pile des appels. Cette durée n’inclut pas le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S, mais elle inclut le temps passé dans les fonctions enfants.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps inclusif d’application**|- Pour la fonction active, temps passé dans la fonction et dans ses fonctions enfants. Cette valeur n’inclut pas le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.<br />- Pour une fonction d’appelant, temps inclusif d’application de la fonction active qui a été générée par les appels de cette fonction d’appelant.<br />- Pour une fonction d’appelé, temps passé dans les instances de cette fonction qui ont été générées par les appels émis par la fonction active. Cette valeur inclut le temps passé dans les fonctions enfants de la fonction d’appelé, mais elle n’inclut pas le temps consacré aux appels émis vers le système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.|  
|**% du temps inclusif d’application**|Pourcentage du temps inclusif écoulé total de l’exécution de profilage passé dans le temps inclusif d’application total de cette fonction dans ce contexte.|  
|**Temps inclusif d’application moy.**|Temps inclusif d’application moyen d’un appel à cette fonction dans ce contexte.|  
|**Temps inclusif d’application max.**|Temps inclusif d’application maximal d’un appel à cette fonction dans ce contexte.|  
|**Temps inclusif d’application min.**|Temps inclusif d’application minimal d’un appel à cette fonction dans ce contexte.|  
  
## <a name="application-exclusive-values"></a>Valeurs de temps exclusif d’application  
 Les valeurs de temps exclusif d’application indiquent le temps passé dans la fonction. Ces valeurs n’incluent ni le temps passé dans les fonctions enfants, ni le temps consacré aux appels émis vers le système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps exclusif d’application**|- Pour la fonction active, temps consacré à l’exécution directe de la fonction. Cette valeur n’inclut ni le temps passé dans les fonctions enfants, ni le temps consacré aux appels émis vers le système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.<br />- Pour une fonction d’appelant, temps exclusif d’application de la fonction active qui a été générée par les appels de cette fonction d’appelant.<br />- Pour une fonction d’appelé, temps passé dans les instances de cette fonction qui ont été générées par les appels émis par la fonction active. Cette valeur n’inclut ni le temps passé dans les fonctions enfants de la fonction d’appelé, ni le temps consacré aux appels émis vers le système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.|  
|**% du temps exclusif d’application**|Pourcentage du temps exclusif écoulé total de l’exécution de profilage passé dans le temps exclusif d’application total de cette fonction dans ce contexte.|  
|**Temps exclusif d’application moy.**|Temps exclusif d’application moyen d’un appel à cette fonction dans ce contexte.|  
|**Temps exclusif d’application max.**|Temps exclusif d’application maximal d’un appel à cette fonction dans ce contexte.|  
|**Temps exclusif d’application min.**|Temps exclusif d’application minimal d’un appel à cette fonction dans ce contexte.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour personnaliser les colonnes de la vue Rapport](../profiling/how-to-customize-report-view-columns.md)   
 [Vue Appelant/Appelé - Données d’échantillonnage](../profiling/caller-callee-view-sampling-data.md)   
 [Vue Appelant/Appelé - Données d’échantillonnage de mémoire .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Vue Appelant/Appelé - Données d’instrumentation de la mémoire .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)