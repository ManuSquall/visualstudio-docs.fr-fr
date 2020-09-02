---
title: Vue Appelant/Appelé - Données d’instrumentation de la mémoire .NET | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: da624c06-8741-4afb-aad1-f8c0002f3de2
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 355ca018f1bf5192d6eb65b3fc218c8d1076563b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176660"
---
# <a name="callercallee-view---net-memory-instrumentation-data"></a>Vue Appelant/Appelé - Données d’instrumentation de la mémoire .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La vue Appelant/Appelé des données de profilage de la mémoire .NET, collectées à l’aide de la méthode d’instrumentation, affiche les données d’allocation et de durée de la fonction sélectionnée et de ses fonctions parents et enfants. La vue Appelant/Appelé comprend trois grilles.  
  
 La grille centrale intitulée **Fonction active** contient les informations de profilage de mémoire associées à la fonction sélectionnée. Ces valeurs incluent tous les appels échantillonnés émis vers la fonction.  
  
 La grille supérieure intitulée **Fonctions qui ont appelé la fonction active** indique la valeur de la fonction sélectionnée (active) qui a été générée par les appels de la fonction d’appelant (parent).  
  
 La grille inférieure intitulée **Fonctions qui ont été appelées par la fonction active** contient les données de profilage de mémoire pour les fonctions d’appelé (enfants) de la fonction sélectionnée lorsque la fonction enfant a été appelée par la fonction active.  
  
 Double-cliquez sur la ligne d’une fonction d’appelant ou d’appelé pour en faire la fonction active.  
  
## <a name="general"></a>Général  
  
|Colonne|Description|  
|------------|-----------------|  
|**Nom de la fonction**|Nom de la fonction.|  
|**Adresse de la fonction**|Adresse de la fonction.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Nombre d’appels**|Nombre total d'appels passés à cette fonction.|  
|**Source File**|Fichier source contenant la définition pour cette fonction.|  
|**Nom du module**|Nom du module qui contient la fonction.|  
|**Chemin du module**|Chemin d’accès du module qui contient la fonction.|  
|**ID de processus**|ID de processus de l’exécution du profilage.|  
|**Nom du processus**|Nom assigné au processus.|  
|**Traitement de sondes du temps exclusif**|Surcharge de temps pour cette fonction qui est provoquée par l’instrumentation. Le traitement de sondes a été soustrait de tous les temps exclusifs.|  
|**Traitement des sondes temps inclus**|Surcharge de temps pour cette fonction et ses fonctions enfants qui est provoquée par l’instrumentation. Le traitement de sondes a été soustrait de tous les temps inclusifs.|  
|**Type**|Contexte de la fonction :<br /><br /> **0** : la fonction active.<br /><br /> **1** : fonction qui appelle la fonction active<br /><br /> **2** : fonction qui est appelée par la fonction active<br /><br /> Uniquement dans les rapports en ligne de commande [VSPerfReport](../profiling/vsperfreport.md).|  
|**Nom de fonction racine**|Nom de la fonction actuelle. Uniquement dans les rapports en ligne de commande [VSPerfReport](../profiling/vsperfreport.md).|  
  
## <a name="net-memory-allocation-values"></a>Valeurs d’allocation de la mémoire .NET  
  
|Colonne|Description|  
|------------|-----------------|  
|**Allocations exclusives**|- Pour la fonction active, nombre d’objets créés lorsque la fonction exécutait du code dans le corps de la fonction (autrement dit, lorsque la fonction se trouvait en haut de la pile des appels). Ce nombre n’inclut pas les objets créés dans les fonctions appelées par cette fonction.<br />- Pour une fonction d’appelant, nombre d’allocations exclusives de la fonction active qui ont été générées par les appels émis à partir de cette fonction d’appelant.<br />- Pour une fonction d’appelé, nombre d’objets créés par les instances de cette fonction qui ont été appelées par la fonction active. Ce nombre n’inclut pas les objets créés par les fonctions appelées par la fonction d’appelé.|  
|**% d’allocations exclusives**|Pourcentage de tous les objets créés lors de l’exécution du profilage qui étaient des allocations exclusives de cette fonction.|  
|**Allocations inclusives**|- Pour la fonction active, nombre d’objets alloués par la fonction dans l’exécution du profilage. Ce nombre inclut les objets créés dans les fonctions d’appelé qui ont été appelées par la fonction.<br />- Pour une fonction d’appelant, nombre d’allocations inclusives de la fonction active qui ont été générées par les appels émis à partir de cette fonction d’appelant.<br />- Pour une fonction d’appelé, nombre d’objets alloués par les instances de cette fonction qui ont été générées par les appels émis par la fonction active. Ce nombre comprend les allocations effectuées par les fonctions qui ont été appelées par cette fonction d’appelé.|  
|**% d’allocations inclusives**|Pourcentage de tous les objets créés lors de l’exécution du profilage qui étaient des allocations inclusives de cette fonction.|  
|**Octets exclusifs**|- Pour la fonction active, nombre d’octets de mémoire alloués par la fonction dans l’exécution du profilage. Ce nombre n’inclut pas la mémoire allouée dans les fonctions d’appelé qui ont été appelées par la fonction.<br />- Pour une fonction d’appelant, nombre d’octets exclusifs de la fonction active qui ont été générés par les appels émis par cette fonction d’appelant.<br />- Pour une fonction d’appelé, nombre d’octets alloués par les instances de cette fonction qui ont été générées par les appels émis par la fonction active. Ce nombre ne comprend pas les octets alloués par les fonctions qui ont été appelées par la fonction d’appelé.|  
|**% d’octets exclusifs**|Pourcentage de tous les octets de mémoire alloués lors de l’exécution du profilage qui étaient des allocations exclusives de cette fonction.|  
|**Octets inclusifs**|- Pour la fonction active, nombre d’octets de mémoire alloués par la fonction dans l’exécution du profilage. Ce nombre inclut la mémoire allouée dans les fonctions d’appelé qui ont été appelées par la fonction.<br />- Pour une fonction d’appelant, nombre d’octets inclusifs des instances de la fonction active qui ont été générées par les appels émis à partir de cette fonction d’appelant.<br />- Pour une fonction d’appelé, nombre d’octets alloués par les instances de cette fonction qui ont été générées par les appels émis par la fonction active. Ce nombre comprend les octets alloués par les fonctions qui ont été appelées par la fonction d’appelé.|  
|**% d’octets inclusifs**|Pourcentage de tous les octets de mémoire alloués lors de l’exécution du profilage qui étaient des allocations inclusives de cette fonction.|  
  
## <a name="elapsed-inclusive-values"></a>Valeurs de temps inclusif écoulé  
 Les valeurs de temps inclusif écoulé indiquent le temps qu’a passé une fonction dans la pile des appels. Cette durée comprend le temps passé dans les fonctions enfants, ainsi que le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps inclusif écoulé**|- Pour la fonction active, temps passé dans la fonction. Cette valeur comprend le temps passé dans les fonctions enfants, ainsi que le temps consacré aux appels émis vers le système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.<br />- Pour une fonction d’appelant, temps inclusif écoulé de la fonction active qui a été générée par les appels de cette fonction d’appelant.<br />- Pour une fonction d’appelé, temps passé dans cette fonction qui a été générée par les appels émis par la fonction active. Cette valeur comprend le temps passé dans les fonctions enfants, ainsi que le temps consacré aux appels émis vers le système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.|  
|**% de temps inclusif écoulé**|Pourcentage du temps inclusif écoulé total de l’exécution de profilage passé dans le temps inclusif écoulé de cette fonction dans ce contexte.|  
|**Temps inclusif écoulé moy.**|Temps inclusif écoulé moyen d’un appel à cette fonction dans ce contexte.|  
|**Temps inclusif écoulé max.**|Temps inclusif écoulé maximal d’un appel à cette fonction dans ce contexte.|  
|**Temps inclusif écoulé min.**|Temps inclusif écoulé minimal d’un appel à cette fonction dans ce contexte.|  
  
## <a name="elapsed-exclusive-values"></a>Valeurs de temps exclusif écoulé  
 Les valeurs de temps exclusif écoulé indiquent la durée pendant laquelle une fonction s’est exécutée directement en haut de la pile des appels. Cette durée inclut le temps consacré aux appels émis vers le système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S, mais elle n’inclut pas le temps passé dans les fonctions enfants.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps exclusif écoulé**|- Pour la fonction active, temps consacré à l’exécution du corps de la fonction. Cette valeur n’inclut pas le temps passé dans les fonctions enfants, mais elle inclut le temps consacré aux appels émis vers le système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.<br />- Pour une fonction d’appelant, temps exclusif écoulé de la fonction active qui a été générée par les appels de cette fonction d’appelant.<br />- Pour une fonction d’appelé, temps passé dans cette fonction qui a été générée par les appels émis par la fonction active. Cette valeur n’inclut pas le temps passé dans les fonctions enfants de la fonction d’appelé, mais elle inclut le temps consacré aux appels émis vers le système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.|  
|**% de temps exclusif écoulé**|Pourcentage du temps exclusif écoulé total de l’exécution de profilage passé dans le temps exclusif écoulé total de cette fonction dans ce contexte.|  
|**Temps exclusif écoulé moy.**|Temps exclusif écoulé moyen d’un appel à cette fonction dans ce contexte.|  
|**Temps exclusif écoulé max.**|Temps exclusif écoulé maximal d’un appel à cette fonction dans ce contexte.|  
|**Temps exclusif écoulé min.**|Temps exclusif écoulé minimal d’un appel à cette fonction dans ce contexte.|  
  
## <a name="application-inclusive-values"></a>Valeurs de temps inclusif d’application  
 Les valeurs de temps inclusif d’application indiquent le temps qu’a passé une fonction dans la pile des appels. Cette durée n’inclut pas le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S, mais elle inclut le temps passé dans les fonctions enfants.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps inclusif d’application**|- Pour la fonction active, temps passé dans la fonction et dans ses fonctions enfants. Cette valeur n’inclut pas le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.<br />- Pour une fonction d’appelant, temps inclusif d’application de la fonction active qui a été générée par les appels de cette fonction d’appelant.<br />- Pour une fonction d’appelé, temps passé dans cette fonction (et ses fonctions enfants) qui a été générée par les appels émis par la fonction active. Cette valeur n’inclut pas le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.|  
|**% du temps inclusif d’application**|Pourcentage du temps inclusif écoulé total de l’exécution de profilage passé dans le temps inclusif d’application total de cette fonction dans ce contexte.|  
|**Temps inclusif d’application moy.**|Temps inclusif d’application moyen d’un appel à cette fonction dans ce contexte.|  
|**Temps inclusif d’application max.**|Temps inclusif d’application maximal d’un appel à cette fonction dans ce contexte.|  
|**Temps inclusif d’application min.**|Temps inclusif d’application minimal d’un appel à cette fonction dans ce contexte.|  
  
## <a name="application-exclusive-values"></a>Valeurs de temps exclusif d’application  
 Les valeurs de temps exclusif d’application indiquent le temps passé dans la fonction, mais pas dans ses fonctions enfants. Cette valeur n’inclut pas non plus le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps exclusif d’application**|- Pour la fonction active, temps consacré à l’exécution du corps de la fonction. Cette valeur n’inclut ni le temps passé dans les fonctions enfants, ni le temps consacré aux appels émis vers le système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.<br />- Pour une fonction d’appelant, temps exclusif d’application de la fonction active qui a été générée par les appels de cette fonction d’appelant.<br />- Pour une fonction d’appelé, temps passé dans cette fonction qui a été générée par les appels émis par la fonction active. Cette valeur n’inclut ni le temps passé dans les fonctions enfants de la fonction d’appelé, ni le temps consacré aux appels émis vers le système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.|  
|**% du temps exclusif d’application**|Pourcentage du temps exclusif écoulé total de l’exécution de profilage passé dans le temps exclusif d’application total de cette fonction dans ce contexte.|  
|**Temps exclusif d’application moy.**|Temps exclusif d’application moyen d’un appel à cette fonction dans ce contexte.|  
|**Temps exclusif d’application max.**|Temps exclusif d’application maximal d’un appel à cette fonction dans ce contexte.|  
|**Temps exclusif d’application min.**|Temps exclusif d’application minimal d’un appel à cette fonction dans ce contexte.|  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : personnaliser les colonnes de la vue rapport](../profiling/how-to-customize-report-view-columns.md)   
 [Vue appelant/appelé-données d’échantillonnage de la mémoire .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Vue appelant/appelé-données d’instrumentation](../profiling/caller-callee-view-instrumentation-data.md)   
 [Vue appelant/appelé-données d’échantillonnage](../profiling/caller-callee-view-sampling-data.md)
