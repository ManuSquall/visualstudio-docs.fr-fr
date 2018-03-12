---
title: "Analyser l’utilisation de mémoire dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: aac1c901f98d63b8cf77b41a165548cccede4f21
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2018
---
# <a name="analyze-memory-usage"></a>Analyser l’utilisation de la mémoire
Utilisez l’outil de diagnostic **Utilisation de la mémoire** intégré au débogueur pour rechercher les fuites de mémoire et les utilisations inefficaces de la mémoire. L’outil Utilisation de la mémoire vous permet de prendre un ou plusieurs *instantanés* du tas de mémoire managée et native. Vous pouvez collecter des instantanés d’applications .NET, natives ou en mode mixte (.NET et native).  
  
-   Vous pouvez analyser un instantané pour comprendre l’impact relatif des types d’objets sur l’utilisation de la mémoire et pour rechercher le code dans votre application qui utilise la mémoire de manière inefficace.  
  
-   Vous pouvez aussi comparer (diff) deux instantanés d’une application pour rechercher les sections de votre code qui provoquent une augmentation de l’utilisation de la mémoire au fil du temps.  

Pour obtenir des instructions détaillées, consultez le didacticiel [Analyser l’utilisation de la mémoire](../profiling/memory-usage.md). Pour analyser l’utilisation de la mémoire sans y attacher le débogueur, consultez [Utilisation de la mémoire sans le débogueur](memory-usage-without-debugging2.md).
  
## <a name="blogs-and-videos"></a>Blogs et vidéos  

|         |         |
|---------|---------|
|  ![Icône représentant une caméra pour les vidéos](../install/media/video-icon.png "Regarder une vidéo")  |    [Regardez une vidéo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Profiling-with-Diagnostics-Tools-in-Visual-Studio-2017-daHnzMD6D_9211787171) sur l’utilisation des outils de diagnostic qui montre comment analyser l’utilisation de la mémoire et l’utilisation de l’UC dans Visual Studio 2017. |

 [Analyser l’UC et la mémoire pendant le débogage](https://blogs.msdn.microsoft.com/visualstudio/2016/02/15/analyze-cpu-memory-while-debugging/)  
  
 [Blog Visual C++ : Profilage de la mémoire dans Visual C++ 2015](https://blogs.msdn.microsoft.com/vcblog/2015/10/21/memory-profiling-in-visual-c-2015/)  

## <a name="see-also"></a>Voir aussi
 [Profilage dans Visual Studio](../profiling/index.md)  
 [Visite guidée des fonctionnalités de profilage](../profiling/profiling-feature-tour.md)