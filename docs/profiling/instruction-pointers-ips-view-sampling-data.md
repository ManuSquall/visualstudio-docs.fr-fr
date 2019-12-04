---
title: Pointeurs d’instruction (IP), vue - Données d’échantillonnage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: c7f647bb-c5a3-4708-9f9d-33c0fd6e2e96
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 42398e044bfc06e41249b15ac9baeebcaebd19f6
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74774254"
---
# <a name="instruction-pointers-ips-view---sampling-data"></a>Pointeurs d’instruction (IP), vue - données d’échantillonnage
La vue Pointeurs d’instruction des données d’échantillonnage répertorie les données de performance pour les instructions d’assembly qui s’exécutaient directement lors de la collecte des échantillons dans le cadre de l’exécution du profilage.

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Colonne|Description|
|------------|-----------------|
|**ID du processus**|ID du processus (PID) de l'exécution du profilage.|
|**Nom du processus**|nom du processus.|
|**Nom de module**|Nom du module qui contient l’instruction.|
|**Chemin de module**|Chemin du module qui contient l’instruction.|
|**Fichier source**|Fichier source qui contient l’instruction.|
|**Nom de la fonction**|Nom de la fonction qui contient l’instruction.|
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|
|**Adresse de la fonction**|Adresse mémoire de départ de la fonction dans le fichier binaire chargé.|
|**Début ligne source**|Numéro de la ligne de début dans le fichier source au niveau duquel cet échantillon a été collecté.|
|**Fin ligne source**|Numéro de ligne de fin dans le fichier source au niveau duquel cet échantillon a été collecté.|
|**Début caractère source**|Décalage du caractère de début dans la ligne de fichier source au niveau de laquelle cet échantillon a été collecté.|
|**Fin du caractère source**|Décalage du caractère de fin dans la ligne de fichier source au niveau de laquelle cet échantillon a été collecté.|
|**Adresse d’instruction**|Adresse de l’instruction dans le fichier binaire chargé.|
|**Échantillons exclusifs**|Nombre total d’échantillons collectés pendant l’exécution de l’instruction.|
|**% d’échantillons exclusifs**|Pourcentage de tous les échantillons collectés pendant l’exécution de l’instruction dans le cadre de l’exécution du profilage.|

## <a name="see-also"></a>Voir aussi
- [Pointeurs d’instruction (IP), vue - échantillonnage](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)
