---
title: Vue pointeurs d’instructions (IP)-données d’échantillonnage de la mémoire .NET
description: La vue IP pour les données de profilage d’allocation de mémoire .NET qui ont été collectées à l’aide de la méthode d’échantillonnage répertorie les instructions d’assembly qui ont alloué de la mémoire.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 51f7c9faee3b93a11b3a2a304654005c80b8ad87
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906836"
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>Pointeurs d’instruction, vue - données d’échantillonnage de la mémoire .NET
La vue Pointeurs d’instruction pour les données de profilage de l’allocation de mémoire de .NET qui ont été collectées avec la méthode d’échantillonnage répertorie les instructions d’assembly qui ont alloué de la mémoire lors de l’exécution du profilage. Les colonnes de la vue indiquent également la taille et le nombre d’allocations.

 Seules les valeurs exclusives apparaissent.

|Colonne|Description|
|------------|-----------------|
|**ID de processus**|ID du processus (PID) de l'exécution du profilage.|
|**Nom du processus**|Nom du processus.|
|**Nom du module**|Nom du module qui contient l’instruction.|
|**Chemin du module**|Chemin du module qui contient l’instruction.|
|**Source File**|Fichier source qui contient l’instruction.|
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
- [Pointeurs d'instruction (IP), vue](../profiling/instruction-pointers-ips-view-sampling-data.md)
