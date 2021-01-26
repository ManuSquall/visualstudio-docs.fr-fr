---
title: Vue Fonctions - Données de conflit | Microsoft Docs
description: Obtenir des détails sur la vue de rapport des fonctions des données de conflit, qui répertorie les fonctions de l’exécution du profilage qui ont été bloquées pendant l’exécution du profilage.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 07f23e38a0d2bc7b538bbe42818ce8a8a2f3d2c1
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801667"
---
# <a name="functions-view---contention-data"></a>Fonctions, vue - données de conflit
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
- [Guide pratique pour personnaliser les colonnes de la vue de rapport](../profiling/how-to-customize-report-view-columns.md)
- [Vue Fonctions](../profiling/functions-view.md)
- [Vue fonctions-Instrumentation](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Vue fonctions-échantillonnage](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Vue Fonctions](../profiling/functions-view-instrumentation-data.md)
- [Vue Fonctions](../profiling/functions-view-sampling-data.md)
