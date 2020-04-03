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
ms.openlocfilehash: 21522ba32990a850a388bfcf69ab239232a2c23d
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638422"
---
# <a name="analyze-memory-usage"></a>Analyser l’utilisation de la mémoire

Pour trouver des fuites de mémoire et une utilisation inefficace de la mémoire, vous pouvez utiliser des outils tels que l’outil ou des outils de diagnostic de l’utilisation de la mémoire intégré au débbugger dans le Profileur de performance, comme l’outil d’allocation d’objets .NET et l’outil d’utilisation de la mémoire post-mortem.

L’outil Utilisation de la mémoire vous permet de prendre un ou plusieurs *instantanés* du tas de mémoire managée et native. Vous pouvez collecter des instantanés d’applications .NET, ASP.NET, natives ou en mode mixte (.NET et natives). **L’outil Memory Use** peut s’exécuter sur un projet Visual Studio ouvert, sur une application Microsoft Store installée ou attaché à une application ou un processus en cours d’exécution. Vous pouvez exécuter **l’outil d’utilisation de la mémoire** avec ou sans débogage. Pour plus d’informations, voir [outils de profilage Run avec ou sans le débbugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Dans le débbugger, vous pouvez activer et désactiver le profilage de la mémoire et voir une ventilation par objet de l’utilisation de la mémoire. Vous pouvez afficher les résultats de l’utilisation de la mémoire lorsque l’exécution est en pause, par exemple à un point d’arrêt.

**L’outil .NET Object Allocation** vous aide à identifier les modèles d’allocation et les anomalies dans votre code .NET. Cet outil ne fonctionne que comme un outil post-mortem. Vous pouvez exécuter cet outil sur des machines locales ou éloignées.

Pour des instructions détaillées qui décrivent comment utiliser les outils d’analyse de mémoire, voir le tutoriel [d’utilisation de](../profiling/memory-usage.md) la mémoire Analyze et [l’outil .NET Object Allocation](../profiling/dotnet-alloc-tool.md).

Vous pouvez utiliser les Outils de profilage sans débogueur avec Windows 7 et les versions ultérieures. Windows 8 et les versions ultérieures sont nécessaires pour exécuter les Outils de profilage avec le débogueur (fenêtre **Outils de diagnostic**).

## <a name="blogs-and-videos"></a>Blogs et vidéos

[Analyser le processeur et la mémoire tout en débogage](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Blog Visual CMD : Profilage de la mémoire dans Visual CMD 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Voir aussi

- [Profilage dans Visual Studio](../profiling/index.yml)
- [Découvrir les outils de profilage](../profiling/profiling-feature-tour.md)
- [Analyser l’utilisation de la mémoire sans débogage](../profiling/memory-usage-without-debugging2.md)
