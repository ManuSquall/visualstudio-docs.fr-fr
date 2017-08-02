---
title: "Nouveautés du profilage | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling
- what's new
ms.assetid: d4736cc8-8961-4089-be9e-d5190ce8353c
caps.latest.revision: 42
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 77e7ce26df70e41e2328442454fe78c7a663f1f3
ms.openlocfilehash: f93c61e084378cd702ea8f190e1661c03bbc9c51
ms.lasthandoff: 03/08/2017

---
# <a name="whats-new-in-profiling-tools-in-includevsdev15miscincludesvsdev15mdmd"></a>Nouveautés des outils de profilage dans [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]
Les outils de diagnostics incluent de nouvelles visualisations pour vous aider à identifier dans votre application les problèmes devant être résolus. Les outils de diagnostics incluent désormais la prise en charge des applications ASP.NET.

Pour plus d’informations, consultez les [Notes de publication pour [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]] (https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#debuggingdiag).

Un onglet **Résumé** a été ajouté aux outils pour vous permettre de vous concentrer sur les domaines clés pour l’analyse des performances. Cet onglet affiche le nombre d’événements qui se sont produits et vous permet de prendre des instantanés du tas et d’autoriser une collecte rapide des données d’utilisation du processeur. Cette vue présente tous les événements [Application Insights](https://azure.microsoft.com/en-us/documentation/articles/app-insights-visual-studio/) ou d’[analyse de l’interface utilisateur](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#UIAnalysis). Pour Visual Studio Enterprise, cette vue affiche en plus les événements IntelliTrace.

![Onglet Résumé des outils de diagnostics](~/profiling/media/DiagToolsSummaryTab-2.png "DiagToolsSummaryTab")

L’outil d’utilisation du processeur a de [nouvelles visualisations](../profiling/Beginners-Guide-to-Performance-Profiling.md) pour vous aider à identifier les fonctions qui sont susceptibles de causer des problèmes de performances. La nouvelle vue **Appelant/Appelé** vous permet d’examiner les coûts des appels de fonction effectués vers et depuis une fonction sélectionnée.

![Outils de diagnostic - Vue Appelant/appelé](~/profiling/media/DiagToolsCallerCallee.png "DiagToolsCallerCallee")
  
## <a name="see-also"></a>Voir aussi  
 [Outils de profilage](../profiling/profiling-tools.md)
