---
title: Vue Fonctions - Données de conflit | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1aaab824f40c0cd6ba0a240a6f3035d7ebcccd00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68141901"
---
# <a name="functions-view---contention-data"></a>Vue Fonctions - Données de conflit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La vue de rapport Fonctions des données de conflit répertorie les fonctions dans l’exécution du profilage dont l’exécution a été bloquée pendant l’exécution du profilage.  
  
 Le tableau suivant explique les valeurs qui sont affichées dans la vue Fonctions d’un fichier de données de profilage collectées avec la méthode de concurrence.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps bloqué exclusif**|Durée pendant laquelle l’exécution du code du corps de cette fonction a été bloquée. Le temps bloqué dans les fonctions qui ont été appelées par la fonction n’est pas inclus.|  
|**% de temps bloqué exclusif**|Pourcentage de tout le temps bloqué dans l’exécution du profilage, qui était du temps bloqué exclusif de cette fonction.|  
|**Conflits exclusifs**|Nombre de fois où l’exécution de code du corps de la fonction a été bloquée. Les conflits dans les fonctions qui ont été appelées par la fonction ne sont pas incluses.|  
|**% de conflits exclusifs**|Pourcentage de tous les conflits dans l’exécution de profilage qui étaient des conflits exclusifs de cette fonction.|  
|**Adresse de la fonction**|Adresse de la fonction.|  
|**Nom de la fonction**|Nom complet de la fonction.|  
|**Temps bloqué inclusif**|Durée pendant laquelle l’exécution de cette fonction ou d’une des fonctions appelées par cette fonction a été bloquée.|  
|**% de temps bloqué inclusif**|Pourcentage de tout le temps bloqué dans l’exécution du profilage, qui était du temps bloqué inclusif de cette fonction ou de ce module.|  
|**Conflits inclusifs**|Nombre de fois où l’exécution de cette fonction ou d’une des fonctions appelées par cette fonction a été bloquée.|  
|**% de conflits inclusifs**|Pourcentage de tous les conflits dans l’exécution du profilage qui étaient des conflits inclusifs de cette fonction ou de ce module.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Nom du module**|Nom du module qui contient la fonction.|  
|**Chemin du module**|Chemin d’accès du module qui contient la fonction.|  
|**ID de processus**|ID du processus (PID) dans lequel la fonction s’exécutait.|  
|**Nom du processus**|Nom du processus.|  
|**Source File**|Fichier source contenant la définition pour cette fonction.|  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : personnaliser les colonnes de la vue rapport](../profiling/how-to-customize-report-view-columns.md)   
 [Mode fonctions](../profiling/functions-view.md)   
 [Vue fonctions-Instrumentation](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Vue fonctions-échantillonnage](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Mode fonctions](../profiling/functions-view-instrumentation-data.md)   
 [Vue Fonctions](../profiling/functions-view-sampling-data.md)
