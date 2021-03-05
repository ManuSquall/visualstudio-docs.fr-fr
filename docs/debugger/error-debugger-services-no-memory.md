---
description: La mémoire des services de débogage est insuffisante et a provoqué l’arrêt de la session de débogage.
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
ms.openlocfilehash: d881248652d644e9a82725b0d083d095ff72f885
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147040"
---
# <a name="debugger-services-running-out-of-memory"></a>Services du débogueur à court de mémoire
La mémoire des services de débogage est insuffisante et a provoqué l’arrêt de la session de débogage.

## <a name="to-investigate-this-error-on-windows"></a>Pour examiner cette erreur sur Windows
- Vous pouvez vérifier le graphique traitement de la mémoire dans la fenêtre **outils de diagnostic** pour voir si l’application cible subit une croissance importante de la mémoire. Si c’est le cas, utilisez l’outil utilisation de la **mémoire** pour diagnostiquer le problème sous-jacent, consultez [analyser l’utilisation](../profiling/memory-usage.md)de la mémoire.

- Si l’application cible ne semble pas consommer beaucoup de mémoire, utilisez la fenêtre **Gestionnaire des tâches** pour vérifier l’utilisation de la mémoire de Visual Studio (devenv.exe), le processus de travail (msvsmon.exe) ou de VS Code (vsdbg.exe/vsdbg-ui.exe) pour déterminer s’il s’agit d’un problème du débogueur. Si le processus qui manque de mémoire est devenv.exe, envisagez de réduire le nombre d’extensions Visual Studio en cours d’exécution.

## <a name="see-also"></a>Voir aussi
- [Billet de blog : analyser l’UC et la mémoire pendant le débogage](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [À propos de la gestion de la mémoire](/windows/win32/memory/about-memory-management)
