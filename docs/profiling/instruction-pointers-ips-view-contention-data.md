---
title: Pointeurs d’instructions (IP), vue - Données de conflit | Microsoft Docs
description: Découvrez comment la vue IP des données de conflit répertorie les données des instructions d’assembly dont l’exécution a été bloquée dans l’exécution du profilage.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: f5e49c24-d4cf-4f87-977d-37e3223d1196
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d3877afb4beb48259d737112d61a36edc7a4fd4d
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721591"
---
# <a name="instruction-pointers-ips-view---contention-data"></a>Pointeurs d’instructions (IP), vue - données de conflit
La vue IP des données de conflit répertorie les données des instructions d’assembly dont l’exécution a été bloquée dans le cadre de l’exécution du profilage.

 Le tableau suivant explique les valeurs des colonnes dans la vue Pointeurs d’instruction.

|Colonne|Description|
|------------|-----------------|
|**Temps bloqué exclusif**|Temps bloqué dans cette fonction.|
|**% de temps bloqué exclusif**|Pourcentage de temps bloqué pendant l’exécution de l’instruction.|
|**Conflits exclusifs**|Nombre de conflits qui se sont produits pendant l’exécution de l’instruction.|
|**% de conflits exclusifs**|Pourcentage de tous les conflits survenus pendant l’exécution de l’instruction dans le cadre de l’exécution du profilage.|
|**Adresse de la fonction**|Adresse mémoire de départ de la fonction dans le fichier binaire chargé.|
|**Nom de la fonction**|Nom de la fonction qui contient l’instruction.|
|**Adresse d’instruction**|Adresse mémoire de l’instruction dans le fichier binaire chargé.|
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|
|**Nom du module**|Nom du module qui contient l’instruction.|
|**Chemin du module**|Chemin du module qui contient l’instruction.|
|**ID de processus**|ID de processus (PID) du processus profilé.|
|**Nom du processus**|Nom du processus.|
|**Début caractère source**|Décalage du caractère dans la ligne de fichier source au niveau duquel cette instruction commence.|
|**Fin du caractère source**|Décalage du caractère dans la ligne de fichier source au niveau duquel cette instruction se termine.|
|**Source File**|Fichier source qui contient l’instruction.|
|**Début ligne source**|Numéro de ligne dans le fichier source au niveau duquel cette instruction commence.|
|**Fin ligne source**|Numéro de ligne dans le fichier source au niveau duquel cette instruction se termine.|

## <a name="see-also"></a>Voir aussi
- [Comment : personnaliser les colonnes de la vue rapport](../profiling/how-to-customize-report-view-columns.md)
- [Pointeurs d'instruction (IP), vue](../profiling/instruction-pointers-ips-view.md)
- [Vue pointeurs d’instructions (IP)-échantillonnage](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)
- [Pointeurs d'instruction (IP), vue](../profiling/instruction-pointers-ips-view-sampling-data.md)
