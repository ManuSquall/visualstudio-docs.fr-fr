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
ms.openlocfilehash: 4f06685be91926e4168c5e4592514469f94da47d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932608"
---
# <a name="analyze-memory-usage"></a>Analyser l’utilisation de la mémoire
Utilisez l’outil de diagnostic **Utilisation de la mémoire** intégré au débogueur pour rechercher les fuites de mémoire et les utilisations inefficaces de la mémoire. L’outil Utilisation de la mémoire vous permet de prendre un ou plusieurs *instantanés* du tas de mémoire managée et native. Vous pouvez collecter des instantanés d’applications .NET, ASP.NET, natives ou en mode mixte (.NET et natives).  
  
-   Vous pouvez analyser un instantané pour comprendre l’impact relatif des types d’objets sur l’utilisation de la mémoire et pour rechercher le code dans votre application qui utilise la mémoire de manière inefficace.  
  
-   Vous pouvez aussi comparer (diff) deux instantanés d’une application pour rechercher les sections de votre code qui provoquent une augmentation de l’utilisation de la mémoire au fil du temps.  

Pour obtenir des instructions détaillées, consultez le didacticiel [Analyser l’utilisation de la mémoire](../profiling/memory-usage.md).  Actuellement, pour mesurer l’utilisation de la mémoire faite par une application .NET Core, vous devez utiliser l’outil avec le débogueur joint. Pour les autres applications managées et natives, vous pouvez utiliser l’outil avec ou sans débogueur.

Vous pouvez utiliser les Outils de profilage sans débogueur avec Windows 7 et les versions ultérieures. Windows 8 et les versions ultérieures sont nécessaires pour exécuter les Outils de profilage avec le débogueur (fenêtre **Outils de diagnostic**).
  
## <a name="blogs-and-videos"></a>Blogs et vidéos  

| | |
|---------|---------|
| ![Icône représentant une caméra pour les vidéos](../install/media/video-icon.png "Regarder une vidéo") | [Regardez une vidéo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Profiling-with-Diagnostics-Tools-in-Visual-Studio-2017-daHnzMD6D_9211787171) sur l’utilisation des outils de diagnostic qui montre comment analyser l’utilisation de la mémoire et l’utilisation de l’UC dans Visual Studio 2017. |

 [Analyser l’UC et la mémoire pendant le débogage](https://blogs.msdn.microsoft.com/visualstudio/2016/02/15/analyze-cpu-memory-while-debugging/)  
  
 [Blog Visual C++ : Profilage de la mémoire dans Visual C++ 2015](https://blogs.msdn.microsoft.com/vcblog/2015/10/21/memory-profiling-in-visual-c-2015/)  

## <a name="see-also"></a>Voir aussi
 [Profilage dans Visual Studio](../profiling/index.md)  
 [Découvrir les outils de profilage](../profiling/profiling-feature-tour.md)