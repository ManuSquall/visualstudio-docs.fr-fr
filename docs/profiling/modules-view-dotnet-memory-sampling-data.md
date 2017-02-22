---
title: "Vue Modules - donn&#233;es d&#39;&#233;chantillonnage de m&#233;moire .NET du profileur | Microsoft Docs"
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
  - "Modules (vue)"
ms.assetid: 9c05b51a-8382-44cf-a8f7-3fabdd2e8f1b
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vue Modules - donn&#233;es d&#39;&#233;chantillonnage de m&#233;moire .NET du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vue Modules des données d'allocation de mémoire .NET collectées à l'aide de la méthode d'échantillonnage regroupe les données de mémoire en fonction des modules exécutés lors de l'exécution du profilage.  Chaque module correspond à la racine d'une arborescence hiérarchique.  Les fonctions du module sont répertoriées sous le nœud du module.  
  
 Les numéros de ligne de fichier source des instructions qui allouent la mémoire apparaissent sous le nœud de fonction, et les adresses des instructions chargées de l'allocation apparaissent sous le nœud de ligne.  Les valeurs inclusives et exclusives sont toujours les mêmes pour les données de ligne et les données d'instruction.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Name**|Nom du module, de la fonction, du numéro de ligne ou de l'adresse d'instruction.|  
|**ID de processus**|ID du processus \(PID\) de l'exécution du profilage.|  
|**Nom du processus**|Nom du processus.|  
|**Nom de module**|Nom du module qui contient la fonction.|  
|**Chemin de module**|Chemin d'accès du module.|  
|**Source File**|Fichier source qui contient la définition de cette fonction.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Allocations inclusives**|-   Pour une fonction, nombre total d'objets créés par la fonction.  Le nombre comprend les objets créés dans les fonctions d'appelé appelées par cette fonction.<br />-   Pour un module, nombre d'objets alloués lors d'une exécution du profilage alors qu'au moins une fonction du module était en cours d'exécution.  Le nombre comprend les objets créés dans les fonctions appelées par les fonctions du module.<br />-   Pour une ligne ou une instruction, nombre total d'objets alloués par la ligne ou l'instruction.|  
|**Allocations inclusives %**|Pourcentage de tous les objets alloués lors de l'exécution du profilage qui étaient des allocations inclusives du module, de la fonction, de la ligne ou de l'instruction.|  
|**Allocations exclusives**|-   Pour la fonction active, nombre d'objets créés lorsque la fonction exécutait du code du corps de la fonction, c'est\-à\-dire lorsque la fonction se situait en haut de la pile des appels.  Ce nombre ne comprend pas les objets créés dans les fonctions appelées par cette fonction.<br />-   Pour un module, somme des allocations exclusives des fonctions dans le module.<br />-   Pour une ligne ou une instruction, nombre total d'objets créés par cette ligne ou cette instruction.|  
|**Allocations exclusives %**|Pourcentage de tous les objets alloués lors de l'exécution du profilage qui étaient des allocations exclusives du module, de la fonction, de la ligne ou de l'instruction.|  
|**Octets inclusifs**|-   Pour une fonction, nombre d'octets alloués par la fonction.  Le nombre comprend les octets alloués dans les fonctions appelées par cette fonction.<br />-   Pour un module, nombre d'octets alloués dans une exécution du profilage lorsqu'au moins une fonction du module s'exécutait.  Le nombre comprend les objets créés dans toutes les fonctions appelées par les fonctions du module.<br />-   Pour une ligne ou une instruction, nombre total d'objets créés par la ligne ou l'instruction.|  
|**Octets inclusifs %**|Pourcentage du nombre total d'octets alloués lors de l'exécution du profilage qui étaient des octets inclusifs du module, de la fonction, de la ligne ou de l'instruction.|  
|**Octets exclusifs**|-   Pour une fonction, nombre total d'octets alloués par la fonction.  Le nombre ne comprend pas les octets alloués dans les fonctions appelées par cette fonction.<br />-   Pour un module, somme des octets exclusifs alloués par les fonctions dans le module.<br />-   Pour une ligne ou une instruction, nombre total d'objets alloués par cette ligne ou cette instruction.|  
|**Octets exclusifs %**|Pourcentage du nombre total d'octets alloués lors de l'exécution du profilage qui étaient des octets exclusifs du module de la fonction, de la ligne ou de l'instruction.|  
  
## Voir aussi  
 [Comment : personnaliser les colonnes de la vue de rapport](../profiling/how-to-customize-report-view-columns.md)   
 [Vue Modules \- instrumentation](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Modules, mode](../profiling/modules-view-sampling-data.md)   
 [Modules, vue](../profiling/modules-view-instrumentation-data.md)