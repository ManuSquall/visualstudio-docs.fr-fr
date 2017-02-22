---
title: "Mode Pointeurs d&#39;instructions (IP) - donn&#233;es d&#39;&#233;chantillonnage de m&#233;moire .NET du profileur | Microsoft Docs"
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
  - "Pointeurs d'instruction (mode)"
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Mode Pointeurs d&#39;instructions (IP) - donn&#233;es d&#39;&#233;chantillonnage de m&#233;moire .NET du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le mode IP des données de profilage d'allocation de mémoire .NET collectées à l'aide de la méthode d'échantillonnage répertorie les instructions d'assembly qui ont alloué de la mémoire pendant l'exécution du profilage.  Les colonnes de la vue répertorient également la taille et le nombre d'allocations.  
  
 Seules les valeurs exclusives sont répertoriées.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**ID de processus**|ID du processus \(PID\) de l'exécution du profilage.|  
|**Nom du processus**|Nom du processus.|  
|**Nom de module**|Nom du module qui contient l'instruction.|  
|**Chemin de module**|Chemin d'accès du module qui contient l'instruction.|  
|**Source File**|Fichier source qui contient l'instruction.|  
|**Nom de la fonction**|Nom de la fonction.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Adresse de la fonction**|Adresse de départ de la fonction.|  
|**Début ligne source**|Numéro de la ligne initiale dans le fichier source à laquelle l'allocation s'est produite.|  
|**Fin ligne source**|Numéro de la ligne de fin dans le fichier source à laquelle l'allocation s'est produite.|  
|**Début caractère source**|Offset du caractère initial dans la ligne de fichier source à laquelle l'allocation s'est produite.|  
|**Fin du caractère source**|Offset du caractère de fin dans la ligne de fichier source à laquelle l'allocation s'est produite.|  
|**Adresse d'instruction**|L'adresse de l'instruction.|  
|**Allocations exclusives**|Nombre total d'objets créés par l'instruction.|  
|**Allocations exclusives %**|Le pourcentage de tous les objets créés dans l'exécution du profilage alloués par l'instruction.|  
|**Octets exclusifs**|Le nombre d'octets de mémoire alloués dans l'exécution du profilage alloués par l'instruction.|  
|**Octets exclusifs %**|Le pourcentage de tous les octets de mémoire alloués dans l'exécution du profilage alloués par l'instruction.|  
  
## Voir aussi  
 [Mode Pointeurs d'instruction \(IP\)](../profiling/instruction-pointers-ips-view-sampling-data.md)