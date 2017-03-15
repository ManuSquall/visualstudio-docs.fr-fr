---
title: "Mode Arborescence des appels - donn&#233;es d&#39;&#233;chantillonnage de la m&#233;moire .NET du profileur | Microsoft Docs"
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
ms.assetid: fbb6cb60-420b-4ca9-8306-2494f7d321fe
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Mode Arborescence des appels - donn&#233;es d&#39;&#233;chantillonnage de la m&#233;moire .NET du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vue Arborescence des appels affiche les chemins d'accès d'exécution des fonctions parcourus dans l'application profilée.  La racine de l'arborescence correspond au point d'entrée de l'application ou du composant.  Chaque nœud de fonction répertorie toutes les fonctions appelées et les données d'allocation de mémoire .NET liées à ces appels de fonction.  
  
 Valeurs dans la vue Arborescence des appels pour les instances de fonction qui ont été appelées par la fonction parente dans l'arborescence des appels.  Les valeurs en pourcentage sont calculées en comparant la valeur de l'instance de la fonction au nombre total ou à la taille des allocations dans l'exécution du profilage.  
  
## Mise en surbrillance du chemin réactif d'exécution  
 La vue Arborescence des appels peut développer et mettre en surbrillance le chemin d'exécution du processus ou de la fonction qui a créé les objets mémoire les plus volumineux ou les plus nombreux.  Pour afficher le chemin le plus actif, cliquez avec le bouton droit sur le processus ou la fonction, puis cliquez sur **Développer le chemin réactif**.  
  
## Définition du nœud racine de l'arborescence des appels  
 Chaque processus de l'exécution du profilage s'affiche sous la forme d'un nœud racine.  Pour définir un autre nœud en tant que nœud initial de la vue Arborescence des appels, cliquez avec le bouton droit sur le nœud que vous souhaitez définir comme nœud initial, puis sélectionnez **Définir la racine**.  
  
 En définissant le nœud racine, vous supprimez toutes les autres entrées de l'affichage, à l'exception de la sous\-arborescence du nœud sélectionné.  Vous pouvez réinitialiser le nœud racine sur le nœud préalablement affiché. Pour ce faire, cliquez avec le bouton droit dans la fenêtre Vue Arborescence des appels et sélectionnez **Réinitialiser la racine**.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**ID de processus**|ID du processus \(PID\) de l'exécution du profilage.|  
|**Nom du processus**|Nom du processus.|  
|**Nom de module**|Nom du module qui contient la fonction.|  
|**Chemin de module**|Chemin d'accès du module qui contient la fonction.|  
|**Source File**|Fichier source qui contient la définition de cette fonction.|  
|**Nom de la fonction**|Nom complet de la fonction.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Adresse de la fonction**|Adresse de la fonction.|  
|**Niveau**|Profondeur de la fonction dans l'arborescence des appels.|  
|**Allocations inclusives**|Nombre d'objets alloués par les instances de cette fonction qui ont été appelées par la fonction parente dans l'arborescence des appels.  Ce nombre inclut les allocations effectuées par des fonctions enfants.|  
|**Allocations inclusives %**|Pourcentage de tous les objets créés dans l'exécution du profilage qui correspondaient à des allocations inclusives de cette fonction.|  
|**Allocations exclusives**|Nombre d'objets alloués par les instances de cette fonction qui ont été appelées par la fonction parente dans l'arborescence des appels.  Ce nombre n'inclut pas les allocations effectuées par des fonctions enfants.|  
|**Allocations exclusives %**|Pourcentage de tous les objets créés lors de l'exécution du profilage qui étaient des allocations exclusives des instances de fonction appelées par la fonction parente dans l'arborescence des appels.|  
|**Octets inclusifs**|Nombre d'octets de mémoire alloués par les instances de cette fonction qui ont été appelées par la fonction parente dans l'arborescence des appels.  Ce nombre inclut les allocations effectuées par des fonctions enfants.|  
|**Octets inclusifs %**|Pourcentage de tous les octets de mémoire alloués dans l'exécution du profilage qui correspondaient à des allocations inclusives de cette fonction.|  
|**Octets exclusifs**|Nombre d'octets de mémoire alloués par les instances de cette fonction qui ont été appelées par la fonction parente dans l'arborescence des appels.  Ce nombre n'inclut pas les allocations effectuées par des fonctions enfants.|  
|**Octets exclusifs %**|Pourcentage de tous les octets de mémoire alloués dans l'exécution du profilage qui correspondaient à des allocations exclusives de cette fonction.|  
  
## Voir aussi  
 [Mode Arborescence des appels \- instrumentation](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Mode Arborescence des appels](../profiling/call-tree-view-sampling-data.md)   
 [Mode Arborescence des appels](../profiling/call-tree-view-instrumentation-data.md)