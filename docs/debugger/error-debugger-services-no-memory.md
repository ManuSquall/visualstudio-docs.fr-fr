---
title: Services qui s’exécutent en dehors de la mémoire du débogueur | Microsoft Docs
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
ms.openlocfilehash: 05664ffd056f69215e6fb00d6d49a59382a3692f
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67854016"
---
# <a name="debugger-services-running-out-of-memory"></a>Services qui s’exécutent en dehors de la mémoire du débogueur
Les Services de débogage a manqué de mémoire et a provoqué l’arrêt de la session de débogage.

## <a name="to-investigate-this-error-on-windows"></a>Pour examiner cette erreur sur Windows
- Vous pouvez vérifier le graphique de mémoire de processus dans le **outils de diagnostic** fenêtre pour voir si l’application cible connaît une croissance importante en mémoire. Dans ce cas, utilisez le **utilisation de la mémoire** outil pour diagnostiquer ce qui est le problème sous-jacent, consultez [analyser l’utilisation de mémoire](../profiling/memory-usage.md).

- Si l’application cible ne semble pas consommer une grande quantité de mémoire, utilisez le **le Gestionnaire des tâches** fenêtre à récupérer de l’utilisation de la mémoire de Visual Studio (devenv.exe), le processus de travail (msvsmon.exe), ou de VS Code (vsdbg.exe/vsdbg-ui.exe) dans déterminer s’il s’agit d’un problème de débogueur. Si le processus manque de mémoire est devenv.exe, envisagez de réduire le nombre d’extensions de Visual Studio en cours d’exécution.

## <a name="see-also"></a>Voir aussi
- [Billet de blog : Analyser l’UC et mémoire pendant le débogage](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [À propos de la gestion de la mémoire](/windows/win32/memory/about-memory-management)
