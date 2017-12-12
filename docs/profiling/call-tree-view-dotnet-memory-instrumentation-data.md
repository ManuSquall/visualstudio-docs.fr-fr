---
title: "Vue Arborescence des appels - Données d’instrumentation de la mémoire .NET | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Call Tree view
ms.assetid: dd359707-245a-4a36-8305-2e980b9edd53
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e77a6a1b97d186cfdc9619fc2d57c05831a752ac
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="call-tree-view---net-memory-instrumentation-data"></a>Vue Arborescence des appels - Données d’instrumentation de la mémoire .NET
La vue Arborescence des appels des données de profilage pour l’allocation de la mémoire .NET qui ont été collectées avec la méthode d’instrumentation montre les chemins d’exécution empruntés par les fonctions dans l’application profilée. La racine de l’arborescence correspond au point d’entrée de l’application ou du composant. Chaque nœud d’une fonction répertorie toutes les fonctions qu’elle a appelées, ainsi que les données concernant la mémoire et la chronologie .NET pour la fonction.  
  
 Les valeurs qui s’affichent dans la vue Arborescence des appels sont celles des instances de fonction qui ont été appelées par la fonction parent dans l’arborescence des appels. Les valeurs en pourcentage sont calculées en comparant la valeur de l’instance de la fonction au nombre total ou à la taille totale des allocations dans l’exécution du profilage.  
  
## <a name="highlighting-the-execution-hot-path"></a>Mise en surbrillance du chemin actif d’exécution  
 La vue Arborescence des appels peut être développée pour mettre en surbrillance le chemin d’exécution du processus ou de la fonction qui a créé les plus grands objets ou le plus d’objets en mémoire. Pour afficher le chemin le plus actif, cliquez avec le bouton droit sur le processus ou la fonction, puis cliquez sur **Développer le chemin réactif**.  
  
## <a name="setting-the-call-tree-root-node"></a>Définition du nœud racine de l’arborescence des appels  
 Chaque processus de l’exécution du profilage s’affiche sous forme de nœud racine. Vous pouvez définir le nœud de départ de la vue Arborescence des appels en cliquant avec le bouton droit sur ce nœud, puis en sélectionnant **Définir la racine**.  
  
 En définissant le nœud racine, vous supprimez toutes les autres entrées de l'affichage, à l'exception de la sous-arborescence du nœud sélectionné. Vous pouvez réinitialiser le nœud racine au nœud examiné à l’origine : cliquez avec le bouton droit dans la fenêtre Vue Arborescence des appels, puis sélectionnez **Réinitialiser la racine**.  
  
## <a name="general"></a>Général  
  
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
|**Nom du processus**|Nom assigné au processus.|  
|**Traitement de sondes du temps exclusif**|Surcharge de temps pour cette fonction qui est provoquée par l'instrumentation. Le traitement de sondes a été soustrait de tous les temps exclusifs.|  
|**Traitement des sondes temps inclus**|Surcharge de temps pour cette fonction et ses fonctions enfants qui est provoquée par l'instrumentation. Le traitement de sondes a été soustrait de tous les temps inclusifs.|  
|**Type**|Contexte de la fonction :<br /><br /> -   **0** : fonction active<br />-   **1** : fonction qui appelle la fonction active<br />-   **2** : fonction qui est appelée par la fonction active<br /><br /> Uniquement dans les rapports en ligne de commande [VSPerfReport](../profiling/vsperfreport.md).|  
|**Nom de fonction racine**|Nom de la fonction active. Uniquement dans les rapports en ligne de commande [VSPerfReport](../profiling/vsperfreport.md).|  
  
## <a name="net-memory-values"></a>Valeurs de mémoire .NET  
 Les valeurs de mémoire .NET inclusives d’une fonction indiquent le nombre (allocations) et la taille (octets) des objets créés par la fonction et les fonctions qui ont été appelées par celle-ci.  
  
 Les valeurs de mémoire exclusives indiquent le nombre et la taille des objets créés par le code du corps de la fonction, mais pas par les fonctions qui ont été appelées par cette fonction.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Allocations inclusives**|Nombre d’objets alloués par les instances de cette fonction qui ont été appelées par la fonction parente dans l’arborescence des appels. Ce nombre comprend les allocations effectuées par des fonctions enfants.|  
|**% d’allocations inclusives**|Pourcentage de tous les objets créés au cours de l’exécution du profilage qui étaient des allocations inclusives des instances de cette fonction appelées par la fonction parente dans l’arborescence des appels.|  
|**Allocations exclusives**|Nombre d’objets alloués par les instances de cette fonction qui ont été appelées par la fonction parente dans l’arborescence des appels. Ce nombre ne comprend pas les allocations effectuées par les fonctions enfants.|  
|**% d’allocations exclusives**|Pourcentage de tous les objets créés au cours de l’exécution du profilage qui étaient des allocations exclusives des instances de cette fonction appelées par la fonction parente dans l’arborescence des appels.|  
  
## <a name="elapsed-inclusive-values"></a>Valeurs de temps inclusif écoulé  
 Les valeurs de temps inclusif écoulé indiquent le temps qu’a passé une fonction dans la pile des appels. Cette durée comprend le temps passé dans les fonctions qui ont été appelées par la fonction, ainsi que les appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps inclusif écoulé**|Temps inclusif écoulé total de tous les appels à cette fonction quand elle a été appelée par la fonction parente dans l’arborescence des appels.|  
|**% de temps inclusif écoulé**|Pourcentage du temps inclusif écoulé total de l’exécution du profilage passé dans le temps inclusif écoulé total de cette fonction quand elle a été appelée par la fonction parente dans l’arborescence des appels.|  
|**Temps inclusif écoulé moy.**|Temps inclusif écoulé moyen d’un appel à cette fonction quand elle a été appelée par la fonction parente dans l’arborescence des appels.|  
|**Temps inclusif écoulé max.**|Temps inclusif écoulé maximal d’un appel à cette fonction quand elle a été appelée par la fonction parente dans l’arborescence des appels.|  
|**Temps inclusif écoulé min.**|Temps inclusif écoulé minimal d’un appel à cette fonction quand elle a été appelée par la fonction parente dans l’arborescence des appels.|  
  
## <a name="elapsed-exclusive-values"></a>Valeurs de temps exclusif écoulé  
 Les valeurs de temps exclusif écoulé indiquent la durée pendant laquelle une fonction s’est exécutée directement en haut de la pile des appels. Cette durée inclut le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S. Toutefois, cette durée n’inclut pas le temps passé dans les fonctions qui ont été appelées par la fonction.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps exclusif écoulé**|Temps exclusif écoulé total de tous les appels à cette fonction quand elle a été appelée par la fonction parente dans l’arborescence des appels.|  
|**% de temps exclusif écoulé**|Pourcentage du temps exclusif écoulé total de l’exécution du profilage passé dans le temps exclusif écoulé total de cette fonction quand elle a été appelée par la fonction parente dans l’arborescence des appels.|  
|**Temps exclusif écoulé moy.**|Temps exclusif écoulé moyen de tous les appels à cette fonction quand elle a été appelée par la fonction parente dans l’arborescence des appels.|  
|**Temps exclusif écoulé max.**|Temps exclusif écoulé maximal de tous les appels à cette fonction quand elle a été appelée par la fonction parente dans l’arborescence des appels.|  
|**Temps exclusif écoulé min.**|Temps exclusif écoulé minimal de tous les appels à cette fonction quand elle a été appelée par la fonction parente dans l’arborescence des appels.|  
  
## <a name="application-inclusive-values"></a>Valeurs de temps inclusif d’application  
 Les valeurs de temps inclusif d’application indiquent le temps qu’a passé une fonction dans la pile des appels. Cette durée n’inclut pas le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S. La durée inclut le temps passé dans les fonctions enfants qui ont été appelées par la fonction.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps inclusif d’application**|Temps inclusif d’application total de tous les appels à cette fonction quand elle a été appelée par la fonction parente dans l’arborescence des appels.|  
|**% du temps inclusif d’application**|Pourcentage du temps inclusif écoulé total de l’exécution du profilage passé dans le temps inclusif d’application total de cette fonction quand elle a été appelée par la fonction parente dans l’arborescence des appels.|  
|**Temps inclusif d’application moy.**|Temps inclusif d’application moyen d’un appel à cette fonction quand elle a été appelée par la fonction parente dans l’arborescence des appels.|  
|**Temps inclusif d’application max.**|Temps inclusif d’application maximal d’un appel à cette fonction quand elle a été appelée par la fonction parente dans l’arborescence des appels.|  
|**Temps inclusif d’application min.**|Temps inclusif d’application minimal d’un appel à cette fonction quand elle a été appelée par la fonction parente dans l’arborescence des appels.|  
  
## <a name="application-exclusive-values"></a>Valeurs de temps exclusif d’application  
 Les valeurs de temps exclusif d’application indiquent le temps passé dans la fonction, en excluant le temps passé dans les fonctions enfants qui ont été appelées par la fonction. La durée exclut également les appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps exclusif d’application**|Temps exclusif d’application total de tous les appels à cette fonction quand elle a été appelée par la fonction parente dans l’arborescence des appels.|  
|**% du temps exclusif d’application**|Pourcentage du temps exclusif écoulé total de l’exécution du profilage passé dans le temps exclusif d’application total de cette fonction quand elle a été appelée par la fonction parente dans l’arborescence des appels.|  
|**Temps exclusif d’application moy.**|Temps exclusif d’application moyen d’un appel à cette fonction quand elle a été appelée par la fonction parente dans l’arborescence des appels.|  
|**Temps exclusif d’application max.**|Temps exclusif d’application maximal d’un appel à cette fonction quand elle a été appelée par la fonction parente dans l’arborescence des appels.|  
|**Temps exclusif d’application min.**|Temps exclusif d’application minimal d’un appel à cette fonction quand elle a été appelée par la fonction parente dans l’arborescence des appels.|