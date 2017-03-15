---
title: "Vue Modules - donn&#233;es de conflit du profileur | Microsoft Docs"
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
ms.assetid: 1a9aa122-2d8f-4a09-b503-92975aa6b648
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Vue Modules - donn&#233;es de conflit du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le mode Modules des données de conflit affiche les données d'accès concurrentiel groupées par les modules échantillonnés dans les données de profilage.  Chaque module correspond à la racine d'une arborescence hiérarchique.  Les fonctions du module dans lequel les événements de conflit se produisent sont répertoriées sous le nœud du module.  
  
 Si la fonction exécutait son propre code lorsqu'un événement de conflit s'est produit, c'est\-à\-dire que la fonction était en haut de la pile des appels, les lignes et adresses d'instruction source qui étaient exécutées sont répertoriées sous le nœud de la fonction.  Dans la mesure où les données sont collectées pour un pointeur d'instruction ou une ligne source lorsque la ligne ou l'instruction est en cours d'exécution, les valeurs inclusives et exclusives sont toujours les mêmes pour les données de ligne et les données d'instruction.  
  
 Le tableau suivant décrit les valeurs des colonnes dans le mode Modules des données de conflit.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps bloqué exclusif**|-   Pour une fonction, temps pendant lequel cette fonction n'a pas pu exécuter le code dans le corps de la fonction.  Le temps bloqué dans les fonctions qui ont été appelées par la fonction n'est pas inclus.<br />-   Pour un module, somme de temps bloqué exclusif des fonctions dans le module.<br />-   Pour une ligne ou une instruction, temps pendant lequel cette ligne ou instruction n'a pas pu être exécutée.|  
|**% de temps bloqué exclusif**|-   Pour une fonction ou un module, pourcentage de tout le temps bloqué au cours de l'exécution du profilage correspondant au temps bloqué exclusif de cette fonction ou module.<br />-   Pour une ligne ou une instruction, pourcentage de tout le temps bloqué au cours de l'exécution du profilage pendant lequel cette ligne ou instruction n'a pas pu être exécutée.|  
|**Conflits exclusifs**|-   Pour une fonction, nombre de fois où cette fonction n'a pas pu exécuter le code dans le corps de la fonction.  Les conflits dans les fonctions qui ont été appelées par la fonction ne sont pas inclus.<br />-   Pour un module, somme des conflits exclusifs des fonctions dans le module.<br />-   Pour une ligne ou une instruction, nombre de fois où cette ligne ou instruction n'a pas pu être exécutée.|  
|**% de conflits exclusifs**|-   Pour une fonction ou un module, pourcentage de tous les conflits au cours de l'exécution du profilage qui correspondaient à des conflits exclusifs de cette fonction ou module.<br />-   Pour une ligne ou une instruction, pourcentage de tous les conflits au cours de l'exécution du profilage qui empêchaient l'exécution de cette ligne ou instruction.|  
|**Temps bloqué inclusif**|-   Pour une fonction, temps pendant lequel cette fonction, ou une fonction qui a été appelée par cette fonction, n'a pas pu être exécutée.<br />-   Pour un module, somme du temps bloqué pendant lequel au moins une fonction de ce module était sur la pile.<br />-   Pour une ligne ou une instruction, temps pendant lequel cette ligne ou instruction n'a pas pu être exécutée.|  
|**% de temps bloqué inclusif**|-   Pour une fonction ou un module, pourcentage de tout le temps bloqué au cours de l'exécution du profilage correspondant au temps bloqué inclusif de cette fonction ou module.<br />-   Pour une ligne ou une instruction, pourcentage de tout le temps bloqué au cours de l'exécution du profilage pendant lequel cette ligne ou instruction a été exécutée.|  
|**Conflits inclusifs**|-   Pour une fonction, nombre de fois où cette fonction, ou une fonction qui a été appelée par cette fonction, n'a pas pu être exécutée.<br />-   Pour un module, nombre de conflits pendant lesquels au moins une fonction de ce module était sur la pile.<br />-   Pour une ligne ou une instruction, nombre de fois où cette ligne ou instruction n'a pas pu être exécutée.|  
|**% de conflits inclusifs**|-   Pour une fonction ou un module, pourcentage de tous les conflits au cours de l'exécution du profilage qui correspondaient à des conflits inclusifs de cette fonction ou module.<br />-   Pour une ligne ou une instruction, pourcentage de tout le temps bloqué au cours de l'exécution du profilage pendant lequel cette ligne ou instruction a été exécutée.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Nom de module**|Nom du module qui contient la fonction, la ligne ou le pointeur d'instruction.|  
|**Chemin de module**|Chemin d'accès du module qui contient le module, la fonction, la ligne ou le pointeur d'instruction.|  
|**Name**|Nom du module ou d'une fonction.|  
|**ID de processus**|ID du processus \(PID\) de l'exécution du profilage.|  
|**Nom du processus**|Nom du processus.|  
|**Source File**|Fichier source qui contient la définition de cette fonction.|  
  
## Voir aussi  
 [Comment : personnaliser les colonnes de la vue de rapport](../profiling/how-to-customize-report-view-columns.md)   
 [Modules, vue](../profiling/modules-view.md)   
 [Vue Modules \- instrumentation](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Vue Modules \- échantillonnage](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Modules, vue](../profiling/modules-view-instrumentation-data.md)   
 [Modules, mode](../profiling/modules-view-sampling-data.md)