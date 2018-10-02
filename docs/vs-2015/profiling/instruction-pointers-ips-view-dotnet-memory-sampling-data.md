---
title: Vue Pointeurs d’instruction - Données d’échantillonnage de la mémoire .NET | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 21141483d462df0faee099c22e2b79fc1718880d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493399"
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>Vue Pointeurs d’instruction - Données d’échantillonnage de la mémoire .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [vue pointeurs d’Instruction (IP) - données d’échantillonnage de mémoire .NET](https://docs.microsoft.com/visualstudio/profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data).  
  
La vue Pointeurs d’instruction pour les données de profilage de l’allocation de mémoire de .NET qui ont été collectées avec la méthode d’échantillonnage répertorie les instructions d’assembly qui ont alloué de la mémoire lors de l’exécution du profilage. Les colonnes de la vue indiquent également la taille et le nombre d’allocations.  
  
 Seules les valeurs exclusives apparaissent.  
  
|Colonne|Description|  
|------------|-----------------|  
|**ID du processus**|ID du processus (PID) de l'exécution du profilage.|  
|**Nom du processus**|Nom du processus.|  
|**Nom du module**|Nom du module qui contient l’instruction.|  
|**Chemin du module**|Chemin du module qui contient l’instruction.|  
|**Fichier source**|Fichier source qui contient l’instruction.|  
|**Nom de la fonction**|Nom de la fonction.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Adresse de la fonction**|Adresse de départ de la fonction.|  
|**Début ligne source**|Numéro de la ligne de début dans le fichier source au niveau duquel l’allocation a eu lieu.|  
|**Fin ligne source**|Numéro de la ligne de fin dans le fichier source au niveau duquel l’allocation a eu lieu.|  
|**Début caractère source**|Décalage du caractère de début dans la ligne de fichier source au niveau de laquelle l’allocation a eu lieu.|  
|**Fin du caractère source**|Décalage du caractère de fin dans la ligne de fichier source au niveau de laquelle l’allocation a eu lieu.|  
|**Adresse d’instruction**|Adresse de l’instruction.|  
|**Allocations exclusives**|Nombre total d’objets qui ont été créés par l’instruction.|  
|**% d’allocations exclusives**|Pourcentage de tous les objets créés lors de l’exécution du profilage et qui ont été alloués par l’instruction.|  
|**Octets exclusifs**|Nombre d’octets de mémoire alloués lors de l’exécution du profilage qui ont été alloués par l’instruction.|  
|**% d’octets exclusifs**|Pourcentage de tous les octets de mémoire alloués lors de l’exécution du profilage qui ont été alloués par l’instruction.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Pointeurs d’instruction (IP)](../profiling/instruction-pointers-ips-view-sampling-data.md)



