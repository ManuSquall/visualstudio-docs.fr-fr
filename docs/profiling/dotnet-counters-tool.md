---
title: Visualiser les compteurs dotnet | Microsoft Docs
description: Apprenez à utiliser l’outil compteurs .NET dans le profileur de performances de Visual Studio.
ms.date: 12/7/2020
ms.topic: conceptual
helpviewer_keywords:
- dotnet, counters, profiling
author: sagar-shetty
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 7a09cc073b2886ab0d374bccaf8b85f3bb729dd7
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97905026"
---
# <a name="visualize-dotnet-counters-from-the-visual-studio-profiler"></a>Visualiser les compteurs dotnet à partir du profileur Visual Studio


L’outil compteurs .NET vous permet de visualiser les [compteurs dotnet](/dotnet/core/diagnostics/dotnet-counters) dans le temps directement à partir du profileur Visual Studio.


> [!NOTE]
> L’outil compteurs .NET nécessite Visual Studio 2019 version 16,7 ou ultérieure et cible .NET Core 3.0 +.

## <a name="setup"></a>Programme d’installation

1. Ouvrez le profileur de performances (**ALT + F2** ou **Debug-> performance Profiler**) dans Visual Studio.

2. Activez la case à cocher **compteurs .net** .

   :::image type="content" source="../profiling/media/dotnet-counters-tool-selected.png" alt-text="Outil compteurs sélectionné.":::

3. Cliquez sur le bouton **Démarrer** pour exécuter l’outil.

Pour plus d’informations sur la façon d’optimiser les performances de l’outil, consultez [optimisation des paramètres du profileur](../profiling/optimize-profiler-settings.md).


## <a name="understand-your-data"></a>Comprendre vos données

Pendant que l’outil collecte des données, vous pouvez voir les valeurs dynamiques des [compteurs dotnet](/dotnet/core/diagnostics/dotnet-counters).

:::image type="content" source="../profiling/media/dotnet-counters-tool-collecting.png" alt-text="Collecte de l’outil de compteur .NET.":::

Vous pouvez également afficher les graphiques des compteurs en activant la case à cocher en regard des noms de compteur. Vous pouvez afficher les graphiques de plusieurs compteurs à la fois.


Une fois que vous avez fini d’exercer votre application et de collecter des données, vous pouvez arrêter la collecte d’un rapport encore plus détaillé. Pour ce faire, appuyez sur le bouton **arrêter la collection** .


Une fois le rapport chargé, vous devez voir un rapport finalisé semblable à celui illustré ci-dessous.

:::image type="content" source="../profiling/media/dotnet-counters-tool-report.png" alt-text="Rapport de l’outil de compteur .NET.":::

Le rapport affiche les valeurs suivantes :

- Min-valeur minimale pour ce compteur dans la plage de temps sélectionnée.
- Max : valeur maximale de ce compteur dans la plage de temps sélectionnée.
- Average : valeur moyenne pour ce compteur dans la plage de temps sélectionnée.

Vous pouvez filtrer ou ajouter des colonnes dans la table en cliquant avec le bouton droit sur les en-têtes de colonne et en sélectionnant un titre.

:::image type="content" source="../profiling/media/dotnet-counters-tool-columns.png" alt-text="Colonnes de l’outil de compteur .NET.":::

Vous pouvez également afficher des graphiques dans le rapport détaillé en activant les cases à cocher en regard de compteurs. Les données des tables représentent par défaut les valeurs de la durée totale de la trace collectée. Pour filtrer les données sur une plage de temps spécifique, cliquez et faites glisser sur les graphiques.

:::image type="content" source="../profiling/media/dotnet-counters-tool-time-filtering.png" alt-text="Filtrage de l’heure de l’outil compteurs .NET.":::

La table est mise à jour avec les valeurs pertinentes pour l’heure sélectionnée dans les graphiques. Utilisez le bouton **effacer la sélection** pour réinitialiser l’intervalle de temps sélectionné à la trace entière.


## <a name="see-also"></a>Voir aussi

- [Optimisation des paramètres du profileur](../profiling/optimize-profiler-settings.md)
- [compteurs dotnet](/dotnet/core/diagnostics/dotnet-counters)
