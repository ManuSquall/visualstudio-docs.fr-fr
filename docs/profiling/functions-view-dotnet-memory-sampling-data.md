---
title: "Mode Fonctions - donn&#233;es d&#39;&#233;chantillonnage de m&#233;moire .NET du profileur | Microsoft Docs"
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
  - "mode Fonctions"
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Mode Fonctions - donn&#233;es d&#39;&#233;chantillonnage de m&#233;moire .NET du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le mode Fonctions des données de profilage d'allocation de mémoire .NET collectées avec la méthode d'échantillonnage répertorie les fonctions qui ont alloué de la mémoire pendant l'exécution du profilage et signale la taille et le nombre d'allocations.  
  
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
|**Allocations inclusives**|Nombre total d'objets alloués dans cette fonction et ses fonctions enfants.|  
|**Allocations inclusives %**|Pourcentage de tous les objets alloués dans l'exécution du profilage qui correspondaient à des allocations inclusives de cette fonction.|  
|**Allocations exclusives**|Nombre d'objets créés lorsque la fonction s'exécutait directement en haut de la pile des appels.  Ce nombre n'inclut pas les objets créés dans les fonctions enfants.|  
|**Allocations exclusives %**|Pourcentage de tous les objets alloués dans l'exécution du profilage qui correspondaient à des allocations exclusives de cette fonction.|  
|**Octets inclusifs**|Nombre d'octets de mémoire alloués par cette fonction et ses fonctions enfants.|  
|**Octets inclusifs %**|Pourcentage de tous les octets de mémoire alloués dans l'exécution du profilage qui correspondaient à des octets inclusifs de cette fonction.|  
|**Octets exclusifs**|Nombre d'octets de mémoire alloués par cette fonction mais pas par ses fonctions enfants.|  
|**Octets exclusifs %**|Pourcentage de tous les octets de mémoire alloués dans l'exécution du profilage qui correspondaient à des octets exclusifs de cette fonction.|  
  
## Voir aussi  
 [Mode Fonctions \- instrumentation](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Mode Fonctions](../profiling/functions-view-sampling-data.md)   
 [Mode Fonction](../profiling/functions-view-instrumentation-data.md)