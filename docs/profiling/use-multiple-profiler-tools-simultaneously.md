---
title: Utilisation simultanée de plusieurs outils de profileur | Microsoft Docs
ms.date: 4/29/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, multiple tools
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: f72757d46496c3990c0a0d4205753d185078eac7
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85332039"
---
# <a name="using-multiple-profiler-tools-simultaneously"></a>Utilisation simultanée de plusieurs outils de profileur

Le profileur de performances a été conçu avec l’idée que plusieurs outils peuvent être utilisés dans la même session pour aider à comprendre les problèmes de performances. La plupart des outils du profileur de performances prennent en charge l’exécution simultanée, par exemple l’utilisation de l' [UC](../profiling/cpu-usage.md), l' [outil .net Async](../profiling/analyze-async.md)et l’outil [de base de données](../profiling/analyze-database.md) . Pour exécuter les outils simultanément dans la même session de diagnostic, activez la case à cocher en regard de celles-ci, puis démarrez la session de diagnostic.

![Concentrateur de diagnostic-tous les outils sélectionnés](../profiling/media/diaghuballtoolsselected.png "Concentrateur de diagnostic-tous les outils sélectionnés")

>[!NOTE]
>Certains outils, tels que l’outil d' [allocation d’objets .net](../profiling/dotnet-alloc-tool.md) , ne peuvent pas être exécutés avec d’autres outils en raison de leur charge élevée ou d’autres limitations techniques.

## <a name="time-filtering"></a>Filtrage de l’heure 

Pendant l’analyse, les opérations de filtrage de l’heure sont appliquées à travers les outils, ce qui vous permet d’utiliser les informations d’un outil pour réduire une plage de temps et filtrer les données dans un autre outil. Cette fonctionnalité permet de guider l’analyse vers des points spécifiques d’une trace et vous aide à comprendre l’état de l’application.

![Filtrage de l’heure du Hub diag](../profiling/media/diaghubtimefiltering.png "Filtrage de l’heure du Hub diag")

## <a name="see-also"></a>Voir aussi

- [Optimisation des paramètres du profileur](../profiling/optimize-profiler-settings.md)
- [Exécution des outils de profilage avec ou sans le débogueur](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Présentation des méthodes de collecte des performances](../profiling/understanding-performance-collection-methods-perf-profiler.md)
