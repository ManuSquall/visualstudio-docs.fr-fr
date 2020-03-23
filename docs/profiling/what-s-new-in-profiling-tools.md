---
title: Nouveautés du profilage dans Visual Studio 2017 │ Microsoft Docs
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling
- what's new
ms.assetid: d4736cc8-8961-4089-be9e-d5190ce8353c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 0512c6e95f0a26184593f7af5ba08c31c33a3299
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "71128336"
---
# <a name="whats-new-in-profiling-tools-in-includevs_dev15"></a>Nouveautés des outils de profilage dans [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Les outils de diagnostics incluent de nouvelles visualisations pour vous aider à identifier dans votre application les problèmes devant être résolus. Les outils de diagnostics incluent désormais la prise en charge des applications ASP.NET.

Pour plus d’informations, voir les [notes de sortie pour [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](/visualstudio/releasenotes/vs2017-relnotes).

Un onglet **Résumé** a été ajouté aux outils pour vous permettre de vous concentrer sur les domaines clés pour l’analyse des performances. Cet onglet affiche le nombre d’événements qui se sont produits et vous permet de prendre des instantanés du tas et d’autoriser une collecte rapide des données d’utilisation du processeur. Cette vue affiche tous [les aperçus de l’application](/azure/azure-monitor/app/visual-studio) ou les événements [d’analyse de l’interface](/visualstudio/releasenotes/vs2017-relnotes) utilisateur. Pour Visual Studio Enterprise, cette vue affiche en plus les événements IntelliTrace.

![Onglet résumé des outils de diagnostic](../profiling/media/diag-tools-summary-tab-2.png "DiagToolsSummaryTab")

L’outil d’utilisation du processeur a de [nouvelles visualisations](../profiling/Beginners-Guide-to-Performance-Profiling.md) pour vous aider à identifier les fonctions qui sont susceptibles de causer des problèmes de performances. La nouvelle vue **Appelant/Appelé** vous permet d’examiner les coûts des appels de fonction effectués vers et depuis une fonction sélectionnée.

![Vue d’appel d’appelant d’outil de diagnostic](../profiling/media/diag-tools-caller-callee-2.png "DiagToolsCallerCallee DiagToolsCallerCallee")

## <a name="see-also"></a>Voir aussi

- [Profilage dans Visual Studio](../profiling/index.yml)
- [Découvrir les outils de profilage](../profiling/profiling-feature-tour.md)