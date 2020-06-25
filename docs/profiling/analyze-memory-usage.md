---
title: Analyser l’utilisation de la mémoire
ms.custom: seodec18
ms.date: 03/30/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c3a072408fd8f166475919d988766fb42fa7c54
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285944"
---
# <a name="analyze-memory-usage"></a>Analyser l’utilisation de la mémoire

Pour rechercher les fuites de mémoire et l’utilisation inefficace de la mémoire, vous pouvez utiliser des outils tels que l’outil d’allocation de mémoire intégré au débogueur ou les outils du profileur de performances, tels que l’outil d’allocation d’objets .NET et l’outil d’utilisation de la mémoire après mortem.

L’outil Utilisation de la mémoire vous permet de prendre un ou plusieurs *instantanés* du tas de mémoire managée et native. Vous pouvez collecter des instantanés d’applications .NET, ASP.NET, natives ou en mode mixte (.NET et natives). L’outil utilisation de la **mémoire** peut s’exécuter sur un projet Visual Studio ouvert, sur une application Microsoft Store installée, ou attaché à une application ou à un processus en cours d’exécution. Vous pouvez exécuter l’outil utilisation de la **mémoire** avec ou sans débogage. Pour plus d’informations, consultez [exécuter les outils de profilage avec ou sans le débogueur](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Dans le débogueur, vous pouvez activer et désactiver le profilage de la mémoire et voir une répartition par objet de l’utilisation de la mémoire. Vous pouvez afficher les résultats de l’utilisation de la mémoire lorsque l’exécution est suspendue, par exemple à un point d’arrêt.

L’outil d' **allocation d’objets .net** vous aide à identifier les modèles d’allocation et les anomalies dans votre code .net. Cet outil s’exécute uniquement comme un outil d’autopsie. Vous pouvez exécuter cet outil sur des ordinateurs locaux ou distants.

Pour obtenir des instructions détaillées qui décrivent comment utiliser les outils d’analyse de la mémoire, consultez le didacticiel [analyse de l’utilisation](../profiling/memory-usage.md) de la mémoire et l' [outil d’allocation d’objets .net](../profiling/dotnet-alloc-tool.md).

Vous pouvez utiliser les Outils de profilage sans débogueur avec Windows 7 et les versions ultérieures. Windows 8 et les versions ultérieures sont nécessaires pour exécuter les Outils de profilage avec le débogueur (fenêtre **Outils de diagnostic**).

## <a name="blogs-and-videos"></a>Blogs et vidéos

[Analyser l’UC et la mémoire pendant le débogage](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Blog Visual C++ : profilage de la mémoire dans Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Voir aussi

- [Profilage dans Visual Studio](../profiling/index.yml)
- [Découvrir les outils de profilage](../profiling/profiling-feature-tour.md)
- [Analyser l’utilisation de la mémoire sans débogage](../profiling/memory-usage-without-debugging2.md)
