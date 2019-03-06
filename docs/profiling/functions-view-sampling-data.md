---
title: Vue Fonctions - Données d’échantillonnage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Functions View
- Functions view
ms.assetid: 029d5ebb-e551-46b0-b64e-2c553d9dbb8e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c734c7eb5ad6aed489d1c6d2ffb8cd774be6fdd7
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56624319"
---
# <a name="functions-view---sampling-data"></a>Fonctions, vue - données d’échantillonnage
La vue de rapport Fonctions de la méthode de profilage par échantillonnage répertorie les fonctions échantillonnées pendant l’exécution du profilage.

> [!NOTE]
>  Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

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
|**Échantillons inclusifs**|Nombre total d’échantillons collectés lorsque cette fonction était en cours d’exécution ; autrement dit, le nombre d’échantillons collectés lorsque cette fonction se trouvait sur la pile des appels. Ce nombre comprend les échantillons collectés lorsque les fonctions appelées par cette fonction étaient en cours d’exécution.|
|**% des échantillons inclusifs**|Pourcentage de tous les échantillons de l’exécution du profilage qui étaient des échantillons inclusifs de cette fonction.|
|**Échantillons exclusifs**|Nombre total d’échantillons collectés lorsque le code du corps de cette fonction était exécuté ; autrement dit, lorsque cette fonction se trouvait en haut de la pile des appels. Ce nombre n’inclut pas les échantillons collectés dans les fonctions appelées par cette fonction.|
|**% d’échantillons exclusifs**|Pourcentage de tous les échantillons de l’exécution du profilage qui étaient des échantillons exclusifs de cette fonction.|

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour personnaliser les colonnes de vue des rapports](../profiling/how-to-customize-report-view-columns.md)
- [Fonctions, vue - instrumentation](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Fonctions, vue - échantillonnage](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Mode Fonctions](../profiling/functions-view-instrumentation-data.md)