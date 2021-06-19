---
title: Analyser l’utilisation de la mémoire
description: Découvrez les outils que vous pouvez utiliser pour rechercher les fuites de mémoire et l’utilisation inefficace de la mémoire, des outils tels que l’outil utilisation de la mémoire et l’outil d’allocation d’objets .NET.
ms.custom: SEO-VS-2020
ms.date: 10/12/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a6af0cd98e69a3c43ba70f5609567243e6285201
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387968"
---
# <a name="analyze-memory-usage"></a>Analyser l’utilisation de la mémoire

Pour rechercher les fuites de mémoire et l’utilisation inefficace de la mémoire, vous pouvez utiliser des outils tels que l’outil d’allocation de mémoire intégré au débogueur ou les outils du profileur de performances, tels que l’outil d’allocation d’objets .NET et l’outil d’utilisation de la mémoire après mortem.

L’outil Utilisation de la mémoire vous permet de prendre un ou plusieurs *instantanés* du tas de mémoire managée et native. Vous pouvez collecter des instantanés d’applications .NET, ASP.NET, C++ ou en mode mixte (.NET et Native). L’outil utilisation de la **mémoire** peut s’exécuter sur un projet Visual Studio ouvert, sur une application Microsoft Store installée, ou attaché à une application ou à un processus en cours d’exécution. Vous pouvez exécuter l’outil utilisation de la **mémoire** avec ou sans débogage. Pour plus d’informations, consultez [exécuter les outils de profilage avec ou sans le débogueur](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Dans le débogueur, vous pouvez activer et désactiver le profilage de la mémoire et voir une répartition par objet de l’utilisation de la mémoire. Vous pouvez afficher les résultats de l’utilisation de la mémoire lorsque l’exécution est suspendue, par exemple à un point d’arrêt.

Les développeurs .NET peuvent choisir entre l’outil d’allocation d’objets .NET ou l’outil utilisation de la [mémoire](../profiling/memory-usage.md) .

- L' [outil d’allocation d’objets .net](../profiling/dotnet-alloc-tool.md) vous aide à identifier les modèles d’allocation et les anomalies dans votre code .net, et vous aide à identifier les problèmes courants avec garbage collection. Cet outil s’exécute uniquement comme un outil d’autopsie. Vous pouvez exécuter cet outil sur des ordinateurs locaux ou distants.
- L' [outil utilisation](../profiling/memory-usage-without-debugging2.md) de la mémoire est utile pour identifier les fuites de mémoire, qui ne sont généralement pas courantes dans les applications .net. Si vous devez utiliser les fonctionnalités du débogueur lors de la vérification de la mémoire, telles que l’exécution pas à pas du code, l’outil d' [utilisation de la mémoire intégré au débogueur](../profiling/memory-usage.md) est recommandé.

Les développeurs C++ peuvent utiliser l’outil d’utilisation de la mémoire intégré au débogueur ou non du débogueur.

- [Analyser l’utilisation de la mémoire avec le débogueur](../profiling/memory-usage.md)
- [Analyser l’utilisation de la mémoire sans débogage](../profiling/memory-usage-without-debugging2.md)

Vous pouvez utiliser les Outils de profilage sans débogueur avec Windows 7 et les versions ultérieures. Windows 8 et les versions ultérieures sont nécessaires pour exécuter les Outils de profilage avec le débogueur (fenêtre **Outils de diagnostic**).

## <a name="blogs-and-videos"></a>Blogs et vidéos

[Analyser l’UC et la mémoire pendant le débogage](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Blog Visual C++ : profilage de la mémoire dans Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Voir aussi

- [Profilage dans Visual Studio](../profiling/index.yml)
- [Découvrir les outils de profilage](../profiling/profiling-feature-tour.md)
