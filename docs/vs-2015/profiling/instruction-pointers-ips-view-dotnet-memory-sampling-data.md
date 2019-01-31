---
title: Vue Pointeurs d’instruction - Données d’échantillonnage de la mémoire .NET | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dd06bc09114785c4359d05e3cda70c3ce7646c9e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54804245"
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>Vue Pointeurs d’instruction - Données d’échantillonnage de la mémoire .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
