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
ms.openlocfilehash: 277401cb8e4e3b90d3543d6f5307452e83d07cc8
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57222621"
---
# <a name="analyze-memory-usage"></a>Analyser l’utilisation de la mémoire
Utilisez l’outil de diagnostic **Utilisation de la mémoire** intégré au débogueur pour rechercher les fuites de mémoire et les utilisations inefficaces de la mémoire. L’outil Utilisation de la mémoire vous permet de prendre un ou plusieurs *instantanés* du tas de mémoire managée et native. Vous pouvez collecter des instantanés d’applications .NET, ASP.NET, natives ou en mode mixte (.NET et natives).

-   Vous pouvez analyser un instantané pour comprendre l’impact relatif des types d’objets sur l’utilisation de la mémoire et pour rechercher le code dans votre application qui utilise la mémoire de manière inefficace.

-   Vous pouvez aussi comparer (diff) deux instantanés d’une application pour rechercher les sections de votre code qui provoquent une augmentation de l’utilisation de la mémoire au fil du temps.

Pour obtenir des instructions détaillées, consultez le didacticiel [Analyser l’utilisation de la mémoire](../profiling/memory-usage.md).  Actuellement, pour mesurer l’utilisation de la mémoire faite par une application .NET Core, vous devez utiliser l’outil avec le débogueur joint. Pour les autres applications managées et natives, vous pouvez utiliser l’outil avec ou sans débogueur.

Vous pouvez utiliser les Outils de profilage sans débogueur avec Windows 7 et les versions ultérieures. Windows 8 et les versions ultérieures sont nécessaires pour exécuter les Outils de profilage avec le débogueur (fenêtre **Outils de diagnostic**).

## <a name="blogs-and-videos"></a>Blogs et vidéos

[Analyser l’UC et la mémoire pendant le débogage](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Blog Visual C++ : Profilage de la mémoire dans Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Voir aussi

- [Profilage dans Visual Studio](../profiling/index.md)
- [Découvrir les outils de profilage](../profiling/profiling-feature-tour.md)