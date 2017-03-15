---
title: "Mode Fonctions - donn&#233;es de conflit du profileur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mode Fonctions"
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Mode Fonctions - donn&#233;es de conflit du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le mode Rapport de Fonctions de données de conflit répertorie les fonctions dans l'exécution du profilage qui n'ont pas pu être exécutées au cours de l'exécution du profilage.  
  
 Le tableau suivant explique les valeurs affichées en mode Fonctions d'un fichier de données de profilage qui a été collecté à l'aide de la méthode de concurrence.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Temps bloqué exclusif**|Durée pendant laquelle cette fonction n'a pas pu exécuter du code dans le corps de la fonction.  Le temps bloqué dans les fonctions qui ont été appelées par la fonction n'est pas inclus.|  
|**% de temps bloqué exclusif**|Pourcentage du temps bloqué total dans l'exécution du profilage correspondant au temps bloqué exclusif de cette fonction.|  
|**Conflits exclusifs**|Nombre de fois où cette fonction n'a pas pu exécuter le code dans le corps de la fonction.  Les conflits dans les fonctions qui ont été appelées par la fonction ne sont pas inclus.|  
|**% de conflits exclusifs**|Pourcentage de tous les conflits dans l'exécution du profilage correspondant à des conflits exclusifs de cette fonction.|  
|**Adresse de la fonction**|Adresse de la fonction.|  
|**Nom de la fonction**|Nom complet de la fonction.|  
|**Temps bloqué inclusif**|Temps pendant lequel cette fonction, ou une fonction qui a été appelée par cette fonction, n'a pas pu être exécutée.|  
|**% de temps bloqué inclusif**|Pourcentage du temps bloqué total dans l'exécution du profilage qui correspond au temps bloqué inclusif de cette fonction ou module.|  
|**Conflits inclusifs**|Nombre de fois où cette fonction, ou une fonction qui a été appelée par cette fonction, n'a pas pu être exécutée.|  
|**% de conflits inclusifs**|Pourcentage de tous les conflits dans l'exécution du profilage correspondant à des conflits inclusifs de cette fonction ou module.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Nom de module**|Nom du module qui contient la fonction.|  
|**Chemin de module**|Chemin d'accès du module qui contient la fonction.|  
|**ID de processus**|ID du processus \(PID\) dans lequel la fonction s'exécutait.|  
|**Nom du processus**|Nom du processus.|  
|**Source File**|Fichier source qui contient la définition de cette fonction.|  
  
## Voir aussi  
 [Comment : personnaliser les colonnes de la vue de rapport](../profiling/how-to-customize-report-view-columns.md)   
 [Mode Fonction](../profiling/functions-view.md)   
 [Mode Fonctions \- instrumentation](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Mode Fonctions \- échantillonnage](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Mode Fonction](../profiling/functions-view-instrumentation-data.md)   
 [Mode Fonctions](../profiling/functions-view-sampling-data.md)