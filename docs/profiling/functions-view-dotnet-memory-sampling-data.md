---
title: "Vue Fonctions - Données d’échantillonnage de mémoire .NET | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Functions view
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 92d2df0182f976af36e9182d080ef6b51130c826
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="functions-view---net-memory-sampling-data"></a>Vue Fonctions - Données d’échantillonnage de la mémoire .NET
La vue Fonctions des données de profilage de l’allocation mémoire .NET qui ont été collectées avec la méthode d’échantillonnage répertorie les fonctions qui ont alloué de la mémoire lors de l’exécution du profilage, et indique la taille et le nombre des allocations.  
  
|Colonne|Description|  
|------------|-----------------|  
|**ID du processus**|ID du processus (PID) de l'exécution du profilage.|  
|**Nom du processus**|Nom du processus.|  
|**Nom du module**|Nom du module qui contient la fonction.|  
|**Chemin de module**|Chemin d’accès du module qui contient la fonction.|  
|**Fichier source**|Fichier source contenant la définition pour cette fonction.|  
|**Nom de la fonction**|Nom complet de la fonction.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Adresse de la fonction**|Adresse de la fonction.|  
|**Allocations inclusives**|Nombre total d’objets alloués dans cette fonction et ses fonctions enfants.|  
|**% d’allocations inclusives**|Pourcentage de tous les objets alloués lors de l’exécution du profilage qui étaient des allocations inclusives de cette fonction.|  
|**Allocations exclusives**|Nombre d’objets créés quand la fonction s’exécutait directement en haut de la pile des appels. Ce nombre n’inclut pas les objets créés dans les fonctions enfants.|  
|**% d’allocations exclusives**|Pourcentage de tous les objets alloués lors de l’exécution du profilage qui étaient des allocations exclusives de cette fonction.|  
|**Octets inclusifs**|Nombre d’octets de mémoire alloués par cette fonction et ses fonctions enfants.|  
|**% d’octets inclusifs**|Pourcentage de tous les octets de mémoire alloués lors de l’exécution du profilage, qui étaient des octets inclusifs de cette fonction.|  
|**Octets exclusifs**|Nombre d’octets de mémoire alloués par cette fonction mais pas par ses fonctions enfants.|  
|**% d’octets exclusifs**|Pourcentage de tous les octets de mémoire alloués lors de l’exécution du profilage, qui étaient des octets exclusifs de cette fonction.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Fonctions - Instrumentation](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Vue Fonctions](../profiling/functions-view-sampling-data.md)   
 [Vue Fonctions](../profiling/functions-view-instrumentation-data.md)