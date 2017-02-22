---
title: "Mode Arborescence des appels - donn&#233;es d&#39;instrumentation de la m&#233;moire .NET du profileur | Microsoft Docs"
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
  - "mode Arborescence des appels"
ms.assetid: dd359707-245a-4a36-8305-2e980b9edd53
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Mode Arborescence des appels - donn&#233;es d&#39;instrumentation de la m&#233;moire .NET du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le mode Arborescence des appels des données de profilage d'allocation de mémoire .NET collectées avec la méthode d'instrumentation affiche les chemins d'accès d'exécution des fonctions parcourus dans l'application profilée.  La racine de l'arborescence correspond au point d'entrée de l'application ou du composant.  Chaque nœud de fonction répertorie toutes les fonctions appelées, ainsi que les données de mémoire .NET de temporisation de la fonction.  
  
 Valeurs dans la vue Arborescence des appels pour les instances de fonction qui ont été appelées par la fonction parente dans l'arborescence des appels.  Les valeurs en pourcentage sont calculées en comparant la valeur de l'instance de la fonction au nombre total ou à la taille des allocations dans l'exécution du profilage.  
  
## Mise en surbrillance du chemin réactif d'exécution  
 La vue Arborescence des appels peut développer et mettre en surbrillance le chemin d'exécution du processus ou de la fonction qui a créé les objets mémoire les plus volumineux ou les plus nombreux.  Pour afficher le chemin le plus actif, cliquez avec le bouton droit sur le processus ou la fonction, puis cliquez sur **Développer le chemin réactif**.  
  
## Définition du nœud racine de l'arborescence des appels  
 Chaque processus de l'exécution du profilage s'affiche sous la forme d'un nœud racine.  Vous pouvez définir le nœud initial du mode Arborescence des appels en cliquant avec le bouton droit sur le nœud que vous souhaitez définir comme nœud initial, puis en sélectionnant **Définir la racine**.  
  
 En définissant le nœud racine, vous supprimez toutes les autres entrées de l'affichage, à l'exception de la sous\-arborescence du nœud sélectionné.  Vous pouvez réinitialiser le nœud racine sur le nœud préalablement affiché. Pour ce faire, cliquez avec le bouton droit dans la fenêtre Vue Arborescence des appels et sélectionnez **Réinitialiser la racine**.  
  
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
|**Nom du processus**|Nom assigné au processus.|  
|**Temps exclusif de charge de la sonde**|Surcharge de temps pour cette fonction provoquée par l'instrumentation.  Le traitement de sondes a été soustrait de tous les temps exclusifs.|  
|**Temps inclusif de charge de la sonde**|Surcharge de temps pour cette fonction et ses fonctions enfants provoquée par l'instrumentation.  Le traitement de sondes a été soustrait de tous les temps inclusifs.|  
|**Type**|Contexte de la fonction :<br /><br /> -   **0** \- fonction active<br />-   **1** \- fonction qui appelle la fonction active<br />-   **2** \- fonction appelée par la fonction active<br /><br /> Uniquement dans les rapports en ligne de commande de [VSPerfReport](../profiling/vsperfreport.md).|  
|**Nom de la fonction racine**|Nom de la fonction actuelle.  Uniquement dans les rapports en ligne de commande de [VSPerfReport](../profiling/vsperfreport.md).|  
  
## Valeurs de mémoire .NET  
 Les valeurs de mémoire .NET inclusives d'une fonction indiquent le nombre \(allocations\) et la taille \(octets\) des objets créés par la fonction et les fonctions appelées par elle.  
  
 Les valeurs de mémoire exclusives indiquent le nombre et la taille des objets créés par le code dans le corps de la fonction et pas par les fonctions appelées par la fonction.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Allocations inclusives**|Nombre d'objets alloués par les instances de cette fonction qui ont été appelées par la fonction parente dans l'arborescence des appels.  Ce nombre inclut les allocations effectuées par des fonctions enfants.|  
|**Allocations inclusives %**|Pourcentage de tous les objets créés lors de l'exécution du profilage qui étaient des allocations inclusives des instances de fonction appelées par la fonction parente dans l'arborescence des appels.|  
|**Allocations exclusives**|Nombre d'objets alloués par les instances de cette fonction qui ont été appelées par la fonction parente dans l'arborescence des appels.  Ce nombre n'inclut pas les allocations effectuées par des fonctions enfants.|  
|**Allocations exclusives %**|Pourcentage de tous les objets créés lors de l'exécution du profilage qui étaient des allocations exclusives des instances de fonction appelées par la fonction parente dans l'arborescence des appels.|  
  
## Valeurs inclusives écoulées  
 Les valeurs inclusives écoulées indiquent la durée pendant laquelle une fonction se trouvait sur la pile des appels.  Cette durée inclut le temps passé dans les fonctions appelées par la fonction et aux appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps inclusif écoulé**|Temps inclusif écoulé total de tous les appels à cette fonction lors de son appel par la fonction parente dans l'arborescence des appels.|  
|**Temps inclusif écoulé en %**|Pourcentage du temps inclusif écoulé total de l'exécution du profilage correspondant au temps inclusif écoulé total de cette fonction lors de son appel par la fonction parente dans l'arborescence des appels.|  
|**Temps inclusif écoulé moy.**|Temps inclusif écoulé moyen d'un appel à cette fonction lors de son appel par la fonction parente dans l'arborescence des appels.|  
|**Temps inclusif écoulé max.**|Temps inclusif écoulé maximal d'un appel à cette fonction lors de son appel par la fonction parente dans l'arborescence des appels.|  
|**Temps inclusif écoulé min.**|Temps inclusif écoulé minimal d'un appel à cette fonction lors de son appel par la fonction parente dans l'arborescence des appels.|  
  
## Valeurs exclusives écoulées  
 Les valeurs exclusives écoulées indiquent la durée pendant laquelle une fonction s'exécutait directement en haut de la pile des appels.  Le temps comprend le temps passé dans les appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.  Cependant, le temps n'inclut pas le temps passé dans les fonctions appelées par la fonction.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps exclusif écoulé**|Temps exclusif écoulé total de tous les appels à cette fonction lors de son appel par la fonction parente dans l'arborescence des appels.|  
|**Temps exclusif écoulé en %**|Pourcentage du temps exclusif écoulé total de l'exécution du profilage correspondant au temps exclusif écoulé total de cette fonction lors de son appel par la fonction parente dans l'arborescence des appels.|  
|**Temps exclusif écoulé moy.**|Temps exclusif écoulé moyen d'un appel à cette fonction lors de son appel par la fonction parente dans l'arborescence des appels.|  
|**Temps exclusif écoulé max.**|Temps exclusif écoulé maximal d'un appel à cette fonction lors de son appel par la fonction parente dans l'arborescence des appels.|  
|**Temps exclusif écoulé min.**|Temps exclusif écoulé minimal d'un appel à cette fonction lors de son appel par la fonction parente dans l'arborescence des appels.|  
  
## Valeurs inclusives d'application  
 Les valeurs inclusives d'application indiquent la durée pendant laquelle une fonction se trouvait sur la pile des appels.  La durée ne comprend pas le temps passé dans les appels au système d'exploitation, comme les opérations de changements de contexte et d'entrée\/sortie.  Le temps inclut le temps passé dans les fonctions enfants appelées par la fonction.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps inclusif d'application**|Temps inclusif d'application total de tous les appels à cette fonction lors de son appel par la fonction parente dans l'arborescence des appels.|  
|**Temps inclusif d'application en %**|Pourcentage du temps inclusif écoulé total de l'exécution du profilage correspondant au temps inclusif d'application total de cette fonction lors de son appel par la fonction parente dans l'arborescence des appels.|  
|**Temps inclusif d'application moy.**|Temps inclusif d'application moyen d'un appel à cette fonction lors de son appel par la fonction parente dans l'arborescence des appels.|  
|**Temps inclusif d'application max.**|Temps inclusif d'application maximal d'un appel à cette fonction lors de son appel par la fonction parente dans l'arborescence des appels.|  
|**Temps inclusif d'application min.**|Temps inclusif d'application minimal d'un appel à cette fonction lors de son appel par la fonction parente dans l'arborescence des appels.|  
  
## Valeurs exclusives d'application  
 Les valeurs exclusives d'application indiquent le temps passé dans la fonction, à l'exclusion du temps passé dans les fonctions enfants appelées par la fonction.  Le temps exclut également les appels au système d'exploitation, tel que les changements de contexte et les opérations d'entrée\/sortie.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps exclusif d'application**|Temps exclusif d'application total de tous les appels à cette fonction lors de son appel par la fonction parente dans l'arborescence des appels.|  
|**Temps exclusif d'application en %**|Pourcentage du temps exclusif écoulé total de l'exécution du profilage correspondant au temps exclusif d'application total de cette fonction lors de son appel par la fonction parente dans l'arborescence des appels.|  
|**Temps exclusif d'application moy.**|Temps exclusif d'application moyen d'un appel à cette fonction lors de son appel par la fonction parente dans l'arborescence des appels.|  
|**Temps exclusif d'application max.**|Temps exclusif d'application maximal d'un appel à cette fonction lors de son appel par la fonction parente dans l'arborescence des appels.|  
|**Temps exclusif d'application min.**|Temps exclusif d'application minimal d'un appel à cette fonction lors de son appel par la fonction parente dans l'arborescence des appels.|