---
title: Vue Fonctions - Données de conflit | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5874ffc7b4d304d1eaacd78032d657fe6ff31d94
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74780050"
---
# <a name="functions-view---contention-data"></a>Fonctions, vue - données de conflit
La vue de rapport Fonctions des données de conflit répertorie les fonctions dans l’exécution du profilage dont l’exécution a été bloquée pendant l’exécution du profilage.

 Le tableau suivant explique les valeurs qui sont affichées dans la vue Fonctions d’un fichier de données de profilage collectées avec la méthode de concurrence.

|Colonne|Description|
|------------|-----------------|
|**Temps bloqué exclusif**|Durée pendant laquelle l’exécution du code du corps de cette fonction a été bloquée. Le temps bloqué dans les fonctions qui ont été appelées par la fonction n’est pas inclus.|
|**% de temps bloqué exclusif**|Pourcentage de tout le temps bloqué dans l’exécution du profilage, qui était du temps bloqué exclusif de cette fonction.|
|**Conflits exclusifs**|Nombre de fois où l’exécution de code du corps de la fonction a été bloquée. Les conflits dans les fonctions qui ont été appelées par la fonction ne sont pas incluses.|
|**% de conflits exclusifs**|Pourcentage de tous les conflits dans l’exécution de profilage qui étaient des conflits exclusifs de cette fonction.|
|**Adresse de la fonction**|Adresse de la fonction.|
|**Nom de la fonction**|Nom complet de la fonction.|
|**Temps bloqué inclusif**|Durée pendant laquelle l’exécution de cette fonction ou d’une des fonctions appelées par cette fonction a été bloquée.|
|**% de temps bloqué inclusif**|Pourcentage de tout le temps bloqué dans l’exécution du profilage, qui était du temps bloqué inclusif de cette fonction ou de ce module.|
|**Conflits inclusifs**|Nombre de fois où l’exécution de cette fonction ou d’une des fonctions appelées par cette fonction a été bloquée.|
|**% de conflits inclusifs**|Pourcentage de tous les conflits dans l’exécution du profilage qui étaient des conflits inclusifs de cette fonction ou de ce module.|
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|
|**Nom de module**|Nom du module qui contient la fonction.|
|**Chemin de module**|Chemin d’accès du module qui contient la fonction.|
|**ID du processus**|ID du processus (PID) dans lequel la fonction s’exécutait.|
|**Nom du processus**|nom du processus.|
|**Fichier source**|Fichier source contenant la définition pour cette fonction.|

## <a name="see-also"></a>Voir aussi
- [Comment : personnaliser les colonnes de la vue rapport](../profiling/how-to-customize-report-view-columns.md)
- [Mode Fonctions](../profiling/functions-view.md)
- [Fonctions, vue - instrumentation](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Fonctions, vue - échantillonnage](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Mode Fonctions](../profiling/functions-view-instrumentation-data.md)
- [Mode Fonctions](../profiling/functions-view-sampling-data.md)
