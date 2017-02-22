---
title: "Mode Appelant/Appel&#233; - donn&#233;es d&#39;&#233;chantillonnage de m&#233;moire .NET du profileur | Microsoft Docs"
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
  - "mode Appelant/Appelé"
ms.assetid: 36f5b4de-5686-4f40-9e72-f4aee27d833c
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Mode Appelant/Appel&#233; - donn&#233;es d&#39;&#233;chantillonnage de m&#233;moire .NET du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le mode Appelant\/Appelé affiche les informations de profilage de la mémoire .NET d'une fonction sélectionnée et ses fonctions parents et enfants.  Le mode Appelant\/Appelé contient trois grilles.  
  
 La **Fonction active** s'affiche dans la grille centrale et contient les informations de profilage de mémoire sur la fonction sélectionnée.  Les valeurs comprennent tous les appels échantillonnés à la fonction.  
  
 **Fonctions qui ont appelé la fonction active** est affiché dans la grille supérieure et indique la quantité de valeur de la fonction sélectionnée \(active\) générée par les appels de la fonction d'appelant \(parent\).  
  
 **Fonctions qui ont été appelées par la fonction active** est affiché dans la grille inférieure et indique les données de profilage de mémoire des fonctions d'appelé \(enfant\) de la fonction sélectionnée lorsque la fonction enfant a été appelée par la fonction active.  
  
 Double\-cliquez sur une ligne de fonction appelant ou appelé pour transformer cette ligne en fonction active.  
  
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
|**Type**|Contexte de la fonction :<br /><br /> **0** \- la fonction active<br /><br /> **1** \- une fonction qui appelle la fonction active<br /><br /> **2** \- une fonction qui est appelée par la fonction active<br /><br /> Uniquement dans les rapports en ligne de commande de [VSPerfReport](../profiling/vsperfreport.md).|  
|**Niveau**|Profondeur de la fonction dans l'arborescence des appels.  Uniquement dans les rapports en ligne de commande de [VSPerfReport](../profiling/vsperfreport.md).|  
|**Allocations inclusives**|-   Pour la fonction active, nombre d'objets alloués par la fonction dans l'exécution du profilage.  Ce nombre inclut les objets créés dans les fonctions d'appelé.<br />-   Pour une fonction d'appelant, nombre d'allocations inclusives de la fonction active générées par les appels de cette fonction.<br />-   Pour une fonction d'appelé, nombre d'objets alloués par les instances de cette fonction appelés par la fonction active.  Le nombre inclut les allocations faites par les fonctions appelées par la fonction d'appelé.|  
|**Allocations inclusives %**|Pourcentage de tous les objets créés dans l'exécution du profilage qui correspondaient à des allocations inclusives de cette fonction.|  
|**Allocations exclusives**|-   Pour la fonction active, nombre d'objets créés lorsque la fonction exécutait du code du corps de la fonction, c'est\-à\-dire lorsque la fonction se situait en haut de la pile des appels.  Ce nombre ne comprend pas les objets créés dans les fonctions appelées par la fonction.<br />-   Pour une fonction d'appelant, nombre d'allocations exclusives de la fonction active générées par les appels de cette fonction.<br />-   Pour une fonction d'appelé, nombre d'objets créés par les instances de cette fonction appelés par la fonction active.  Le nombre ne comprend pas les objets créés par les fonctions appelées par la fonction d'appelé.|  
|**Allocations exclusives %**|Pourcentage de tous les objets créés dans l'exécution du profilage qui correspondaient à des allocations inclusives de cette fonction.|  
|**Octets inclusifs**|-   Pour la fonction actuelle, nombre d'octets de mémoire alloués par la fonction dans l'exécution du profilage.  Le nombre comprend la mémoire allouée dans les fonctions appelées par cette fonction.<br />-   Pour une fonction d'appelant, nombre d'octets inclusifs de la fonction active générés par les appels via la fonction d'appelant.<br />-   Pour une fonction d'appelé, nombre d'octets alloués par les instances de cette fonction qui ont été générées par des appels de la fonction active.  Ce nombre comprend les octets alloués par les fonctions appelées par la fonction d'appelé.|  
|**Octets inclusifs %**|Pourcentage de tous les octets de mémoire alloués dans l'exécution du profilage qui correspondaient à des allocations inclusives de cette fonction.|  
|**Octets exclusifs**|-   Pour la fonction actuelle, nombre d'octets de mémoire alloués par la fonction dans l'exécution du profilage.  Ce nombre ne comprend pas la mémoire qui a été allouée par les fonctions appelées par la fonction active.<br />-   Pour une fonction d'appelant, nombre d'octets exclusifs de la fonction active générés par les appels de la fonction d'appelant.<br />-   Pour une fonction d'appelé, nombre d'octets alloués par les instances de la fonction qui ont été générées par des appels de la fonction active.  Ce nombre ne comprend pas les octets alloués par les fonctions appelées par la fonction d'appelé.|  
|**Octets exclusifs %**|Pourcentage de tous les octets de mémoire alloués dans l'exécution du profilage qui correspondaient à des allocations exclusives de cette fonction.|  
  
## Voir aussi  
 [Comment : personnaliser les colonnes de la vue de rapport](../profiling/how-to-customize-report-view-columns.md)   
 [Mode Appelant\/Appelé \- instrumentation](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Mode Appelant\/Appelé](../profiling/caller-callee-view-sampling-data.md)   
 [Mode Appelant\/Appelé](../profiling/caller-callee-view-instrumentation-data.md)