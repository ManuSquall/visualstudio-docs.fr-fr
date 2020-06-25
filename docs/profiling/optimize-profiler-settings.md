---
title: Optimisation des paramètres du profileur | Microsoft Docs
ms.date: 4/29/2020
ms.topic: conceptual
helpviewer_keywords:
- Profiler, improve performance
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 9ff76364026230d08d03c91d14bddba3c325e7be
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290407"
---
# <a name="optimizing-profiler-settings"></a>Optimisation des paramètres du profileur

Le profileur de performances et la fenêtre de Outils de diagnostic dans Visual Studio présentent de nombreux paramètres différents qui affectent les performances globales des outils. La modification de certains paramètres peut entraîner l’exécution rapide de l’analyse ou entraîner des temps d’attente supplémentaires lors du traitement des résultats dans les outils. Vous trouverez ci-dessous un résumé de certains paramètres et de leur impact sur les performances.

## <a name="symbol-settings"></a>Paramètres des symboles

Les paramètres de symboles trouvés dans les options du débogueur (**options de débogage > > symboles**) ont un impact significatif sur la durée nécessaire à la génération des résultats dans les outils. L’activation des serveurs de symboles ou l’utilisation du **_NT_SYMBOL_PATH** amène le profileur à demander des symboles pour chaque module chargé dans un rapport. Actuellement, le profileur charge toujours automatiquement tous les symboles, quelle que soit la préférence de chargement automatique des symboles.

![Page chargement de symboles](../profiling/media/symbolloading.png "Chargement de symboles")

La progression du chargement des symboles peut être consultée dans la fenêtre **sortie** sous l’en-tête **outils de diagnostic** .

![Progression du chargement des symboles](../profiling/media/symbolloadingprogress.png "Progression du chargement des symboles")

Une fois téléchargés, les symboles sont mis en cache, ce qui accélère l’analyse future tout en nécessitant le chargement et l’analyse des fichiers. Si le chargement de symboles ralentit l’analyse, essayez de désactiver les serveurs de symboles et d’effacer le cache de symboles. À la place, reposez-vous sur les symboles générés localement pour votre projet.

## <a name="show-external-code"></a>Afficher le code externe

La plupart des outils du **profileur de performances** et de la fenêtre de **outils de diagnostic** ont un concept de code utilisateur et de code externe. Le code utilisateur est tout code généré par la solution ouverte ou l’espace de travail ouvert. Le code externe est autre chose. En gardant le paramètre **afficher le code externe** désactivé ou **afficher uniquement mon code** activé, vous autorisez les outils à agréger du code externe sur une seule image de premier niveau, ce qui réduit considérablement la quantité de traitement requise pour afficher les résultats. Cela permet aux utilisateurs de voir ce qui a été appelé dans le code externe qui a créé le ralenti tout en conservant le traitement des données au minimum. Lorsque cela est possible, laissez l' **afficher le code externe** désactivé et assurez-vous que la solution ou l’espace de travail est ouvert pour le diagsession que vous analysez.

## <a name="trace-duration"></a>Durée de la trace

Le profilage de plus petites durées entraîne moins de données, ce qui est plus rapide à analyser. En général, nous vous recommandons d’essayer de limiter les traces à cinq minutes de données de performances. Certains outils, tels que l’outil utilisation de l' [UC](../profiling/cpu-usage.md) , vous permettent de suspendre la collecte de données pendant que l’outil est en cours d’exécution, afin que vous puissiez limiter la quantité de données collectées dans le scénario que vous souhaitez analyser.

## <a name="sampling-frequency"></a>Fréquence d’échantillonnage

Certains outils, tels que l’outil utilisation de l' [UC](../profiling/cpu-usage.md) et l’outil d' [allocation d’objets net](../profiling/dotnet-alloc-tool.md) , vous permettent d’ajuster une fréquence d’échantillonnage. L’augmentation de cette fréquence d’échantillonnage vous permet de mesurer plus précisément, mais augmente la quantité de données générées. En règle générale, il est préférable de conserver ce paramètre au taux par défaut, sauf si un problème spécifique est étudié.

![Page des propriétés du Hub diag](../profiling/media/diaghubpropertiespage.png "Page des propriétés du Hub diag")

## <a name="see-also"></a>Voir aussi

- [Exécution des outils de profilage avec ou sans le débogueur](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Utilisation simultanée de plusieurs outils de profileur](../profiling/use-multiple-profiler-tools-simultaneously.md)
- [Présentation des méthodes de collecte des performances](../profiling/understanding-performance-collection-methods-perf-profiler.md)
