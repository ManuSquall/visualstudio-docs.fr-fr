---
title: "Mode Pointeurs d&#39;instructions (IP) - donn&#233;es de conflit du profileur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Pointeurs d'instruction (mode)"
ms.assetid: f5e49c24-d4cf-4f87-977d-37e3223d1196
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Mode Pointeurs d&#39;instructions (IP) - donn&#233;es de conflit du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le mode Pointeurs d'instruction des données de conflit répertorie les données des instructions d'assembly dont l'exécution a été bloquée lors de l'exécution du profilage.  
  
 La table suivante explique les valeurs des colonnes du mode Pointeurs d'instruction.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps bloqué exclusif**|Temps bloqué dans cette fonction.|  
|**% de temps bloqué exclusif**|Pourcentage de temps bloqué pendant l'exécution de l'instruction.|  
|**Conflits exclusifs**|Nombre de conflits qui se sont produits pendant l'exécution de l'instruction.|  
|**% de conflits exclusifs**|Pourcentage de tous les conflits survenus pendant l'exécution de l'instruction dans le cadre de l'exécution du profilage.|  
|**Adresse de la fonction**|Adresse mémoire de début de la fonction dans le binaire chargé.|  
|**Nom de la fonction**|Nom de la fonction qui contient l'instruction.|  
|**Adresse d'instruction**|Adresse mémoire de l'instruction dans le binaire chargé.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Nom de module**|Nom du module qui contient l'instruction.|  
|**Chemin de module**|Chemin d'accès du module qui contient l'instruction.|  
|**ID de processus**|ID du processus \(PID\) du processus profilé.|  
|**Nom du processus**|Nom du processus.|  
|**Début caractère source**|Offset du caractère dans la ligne de fichier source au niveau de laquelle cette instruction démarre.|  
|**Fin du caractère source**|Offset du caractère dans la ligne de fichier source au niveau de laquelle cette instruction se termine.|  
|**Source File**|Fichier source qui contient l'instruction.|  
|**Début ligne source**|Numéro de ligne dans le fichier source au niveau duquel cette instruction démarre.|  
|**Fin ligne source**|Numéro de ligne dans le fichier source au niveau duquel cette instruction se termine.|  
  
## Voir aussi  
 [Comment : personnaliser les colonnes de la vue de rapport](../profiling/how-to-customize-report-view-columns.md)   
 [Mode Pointeurs d'instruction \(IP\)](../profiling/instruction-pointers-ips-view.md)   
 [Mode Pointeurs d'instruction \(IP\) \- échantillonnage](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)   
 [Mode Pointeurs d'instruction \(IP\)](../profiling/instruction-pointers-ips-view-sampling-data.md)