---
title: Les services du débogueur manquent de mémoire | Microsoft Docs
ms.date: 07/10/2019
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.debug_no_memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger
author: isadorasophia
ms.author: isgarcia
manager: caslan
ms.workload:
- multiple
ms.openlocfilehash: 12215f9c740e68c4f2749a51b06c09a1385dae1a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737841"
---
# <a name="debugger-services-running-out-of-memory"></a>Services du débogueur à court de mémoire
La mémoire des services de débogage est insuffisante et a provoqué l’arrêt de la session de débogage.

## <a name="to-investigate-this-error-on-windows"></a>Pour examiner cette erreur sur Windows
- Vous pouvez vérifier le graphique traitement de la mémoire dans la fenêtre **outils de diagnostic** pour voir si l’application cible subit une croissance importante de la mémoire. Si c’est le cas, utilisez l’outil utilisation de la **mémoire** pour diagnostiquer le problème sous-jacent, consultez [analyser l’utilisation](../profiling/memory-usage.md)de la mémoire.

- Si l’application cible ne semble pas consommer beaucoup de mémoire, utilisez la fenêtre **Gestionnaire des tâches** pour vérifier l’utilisation de la mémoire de Visual Studio (devenv. exe), le processus de travail (msvsmon. exe) ou de vs code (vsdbg. exe/vsdbg-UI. exe) pour déterminer s’il s’agit d’un problème du débogueur. Si le processus ne dispose pas de suffisamment de mémoire, essayez de réduire le nombre d’extensions Visual Studio en cours d’exécution.

## <a name="see-also"></a>Voir aussi
- [Billet de blog : analyser l’UC et la mémoire pendant le débogage](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [À propos de la gestion de la mémoire](/windows/win32/memory/about-memory-management)
