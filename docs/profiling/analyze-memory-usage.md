---
title: Analyser l’utilisation de la mémoire
ms.custom: seodec18
ms.date: 01/02/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ddb082bf2451759be239d5c16404e82bcd84733
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578158"
---
# <a name="analyze-memory-usage"></a>Analyser l’utilisation de la mémoire

pour rechercher les fuites de mémoire et l’utilisation inefficace de la mémoire, vous pouvez utiliser des outils tels que l’outil d’allocation de mémoire intégré au débogueur ou les outils du profileur de performances, tels que l’outil d’allocation d’objets .NET et l’outil d’utilisation de la mémoire après mortem. L’outil Utilisation de la mémoire vous permet de prendre un ou plusieurs *instantanés* du tas de mémoire managée et native. Vous pouvez collecter des instantanés d’applications .NET, ASP.NET, natives ou en mode mixte (.NET et natives). 

L’outil utilisation de la **mémoire** peut s’exécuter sur un projet Visual Studio ouvert, sur une application Microsoft Store installée, ou attaché à une application ou à un processus en cours d’exécution. Vous pouvez exécuter l’outil sur des ordinateurs locaux ou distants, ou sur un simulateur ou un émulateur. Pour plus d’informations, consultez [Exécution des outils de profilage avec ou sans débogueur](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

Vous pouvez exécuter l’outil utilisation de la **mémoire** avec ou sans débogage. Dans le débogueur, vous pouvez activer et désactiver le profilage de la mémoire et voir une répartition par objet de l’utilisation de la mémoire. Vous pouvez afficher les résultats de l’utilisation de la mémoire lorsque l’exécution est suspendue, par exemple à un point d’arrêt.

L’outil d' **allocation d’objets .net** s’exécute uniquement comme un outil d’autopsie.

Pour obtenir des instructions détaillées qui décrivent comment utiliser les outils d’analyse de la mémoire, consultez le didacticiel [analyse de l’utilisation](../profiling/memory-usage.md) de la mémoire et l' [outil d’allocation d’objets .net](../profiling/dotnet-alloc-tool.md).

Vous pouvez utiliser les Outils de profilage sans débogueur avec Windows 7 et les versions ultérieures. Windows 8 et les versions ultérieures sont nécessaires pour exécuter les Outils de profilage avec le débogueur (fenêtre **Outils de diagnostic**).

## <a name="blogs-and-videos"></a>Blogs et vidéos

[Analyser l’UC et la mémoire pendant le débogage](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Blog Visual C++ : Profilage de la mémoire dans Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Voir aussi

- [Profilage dans Visual Studio](../profiling/index.yml)
- [Découvrir les outils de profilage](../profiling/profiling-feature-tour.md)
- [Analyser l’utilisation de la mémoire sans le débogueur](../profiling/memory-usage-without-debugging2.md)
