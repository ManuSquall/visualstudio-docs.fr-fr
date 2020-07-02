---
title: Mesurer l’utilisation de l’UC dans vos applications
description: Analysez les problèmes de performances de l’UC dans votre application en utilisant les outils de diagnostics intégrés au débogueur.
ms.custom: seodec18
ms.date: 04/03/2019
ms.topic: tutorial
f1_keywords:
- vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
- CPU Usage
- Diagnostics Tools
ms.assetid: da2fbf8a-2d41-4654-a509-dd238532d25a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3a7c5eb8aa489da9ced0803e0f83855734825ff
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537369"
---
# <a name="measure-application-performance-by-analyzing-cpu-usage"></a>Mesurer les performances d’application en analysant l’utilisation de l’UC

Vous pouvez utiliser les outils de profilage de Visual Studio pour analyser les problèmes de performances dans votre application. Cet article explique comment utiliser l’onglet utilisation de l' **UC** des outils de diagnostic pour obtenir des données de performances pour votre application.

Quand le débogueur est suspendu, l’outil **Utilisation de l’UC** collecte les informations relatives aux fonctions qui s’exécutent dans votre application. L’outil répertorie les fonctions qui ont effectué un travail et fournit un graphique chronologique que vous pouvez utiliser pour examiner des segments spécifiques d’une session d’échantillonnage.

Le hub de diagnostic propose de nombreuses autres options pour exécuter et gérer votre session de diagnostic. Si l’outil **Utilisation de l’UC** ne vous fournit pas les données dont vous avez besoin, les [autres outils de profilage](../profiling/profiling-feature-tour.md) fournissent des types d’informations différents qui peuvent vous être utiles. Dans de nombreux cas, le goulot d’étranglement des performances de votre application peut ne pas provenir de votre processeur, mais de la mémoire, de l’interface utilisateur de rendu ou du temps de requête réseau. Le hub de diagnostic vous offre de nombreuses autres options pour enregistrer et analyser ce type de données.

> [!Important]
> Les outils de diagnostics sont pris en charge pour le développement .NET dans Visual Studio (y compris ASP.NET) et pour le développement natif/C++.

Dans cet article, nous allons décrire l’analyse de l’utilisation de l’UC dans un flux de travail de débogage normal. Vous pouvez également analyser l’utilisation de l’UC sans débogueur ou en ciblant une application en cours d’exécution. Pour plus d’informations, consultez [exécuter les outils de profilage avec ou sans le débogueur](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Vous pouvez également utiliser un autre outil de profilage, [PerfTips](../profiling/perftips.md), pour effectuer un pas à pas détaillé dans le code et identifier le temps nécessaire à l’exécution de fonctions ou de blocs de code particuliers.

Vous pouvez utiliser les Outils de profilage sans débogueur avec Windows 7 et les versions ultérieures. Windows 8 et les versions ultérieures sont nécessaires pour exécuter les Outils de profilage avec le débogueur (fenêtre **Outils de diagnostic**).

Ce didacticiel présente les procédures suivantes :

> [!div class="checklist"]
> * Collecter les données d'utilisation de l'UC
> * Analyser les données d’utilisation de l’UC

## <a name="step-1-collect-profiling-data"></a>Étape 1 : Collecter les données de profilage

1. Ouvrez le projet que vous voulez déboguer dans Visual Studio, puis définissez un point d’arrêt dans votre application à l’endroit où vous souhaitez examiner l’utilisation du processeur.

2. Définissez un deuxième point d’arrêt à la fin de la fonction ou de la région de code que vous souhaitez analyser.

    En définissant deux points d’arrêt, vous limitez la collecte de données aux sections de code que vous souhaitez analyser.

3. La fenêtre **outils de diagnostic** s’affiche automatiquement, sauf si vous l’avez désactivée. Pour afficher à nouveau la fenêtre, cliquez sur **Déboguer**  >  **fenêtres**  >  **afficher les outils de diagnostic**.

4. Vous pouvez choisir d’afficher **Utilisation de la mémoire**, [Utilisation de l’UC](../profiling/Memory-Usage.md) ou les deux, avec le paramètre **Sélectionner les outils** de la barre d’outils. Si vous exécutez Visual Studio Enterprise, vous pouvez également activer ou désactiver IntelliTrace dans **Outils**  >  **options**  >  **IntelliTrace**.

     ![Afficher les outils de diagnostic](../profiling/media/diag-tools-select-tool.png "DiagToolsSelectTool")

     Nous allons nous intéresser principalement à l’utilisation du processeur. Vérifiez donc que l’outil **Utilisation de l’UC** est activé (il est activé par défaut).

5. Cliquez sur **Déboguer**  >  **Démarrer le débogage** (ou **Démarrer** dans la barre d’outils, ou **F5**).

     Lorsque l’application est chargée, la vue Résumé des outils de diagnostics s’affiche. Si vous avez besoin d’ouvrir la fenêtre, cliquez sur **Déboguer**  >  **fenêtres**  >  **afficher les outils de diagnostic**.

     ![Onglet Résumé des outils de diagnostic](../profiling/media/diag-tools-summary-tab.png "DiagToolsSummaryTab")

     Pour plus d’informations sur les événements, consultez [recherche et filtrage de l’onglet événements de la fenêtre outils de diagnostic](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

6. Exécutez le scénario qui doit provoquer le premier point d’arrêt.

7. Pendant que le débogueur est suspendu, activez la collecte des données d’utilisation du processeur, puis ouvrez l’onglet **Utilisation de l’UC**.

     ![Les outils de diagnostics activent le profilage de l’UC](../profiling/media/diag-tools-enable-cpu-profiling.png "DiagToolsEnableCPUProfiling")

     Quand vous choisissez **Enregistrer le profil du processeur**, Visual Studio commence à enregistrer vos fonctions, ainsi que la durée de leur exécution. Vous pouvez uniquement afficher les données collectées lorsque votre application s’interrompt à un point d’arrêt.

8. Appuyez sur F5 pour exécuter l’application jusqu’au deuxième point d’arrêt.

     Vous disposez maintenant de données de performances pour votre application, et plus spécifiquement pour la région de code qui s’exécute entre les deux points d’arrêt.

     Le profileur commence la préparation des données de thread. Attendez qu’elle se termine.

     ![Outils de diagnostics préparation des threads](../profiling/media/diag-tools-preparing-data.png "DiagToolsPreparingThreads")

     L’outil Utilisation de l’UC affiche le rapport sous l’onglet **Utilisation de l’UC**.

     ![Onglet utilisation de l’UC des outils de diagnostic](../profiling/media/diag-tools-cpu-usage-tab.png "DiagToolsCPUUsageTab")

9. Si vous souhaitez analyser une région de code plus spécifique, sélectionnez une région (qui affiche les données de profilage) dans la chronologie du processeur.

     ![Outils de diagnostic sélectionnant un segment de temps](../profiling/media/diag-tools-select-time-segment.png "DiagToolsSelectTimeSegment")

     À ce stade, vous pouvez commencer à analyser les données.

     > [!TIP]
     >  Lorsque vous tentez d’identifier les problèmes de performances, effectuez plusieurs mesures. Les performances varient naturellement d’une exécution à l’autre, et les chemins de code s’exécutent généralement plus lentement la première fois qu’ils s’exécutent en raison d’un travail d’initialisation unique, tel que le chargement des dll, la compilation JIT des méthodes et l’initialisation des caches. En effectuant plusieurs mesures, vous avez une meilleure idée de la plage et de la valeur médiane de la mesure affichée, ce qui vous permet de comparer la première fois et les performances d’état stable d’une zone de code.

## <a name="step-2-analyze-cpu-usage-data"></a>Étape 2 : Analyser les données d’utilisation de l’UC

Nous vous recommandons de commencer à analyser vos données en examinant la liste des fonctions située sous l’onglet Utilisation de l’UC, en identifiant les fonctions qui effectuent la plus grande partie du travail, puis en analysant ces fonctions les unes après les autres.

1. Dans la liste des fonctions, examinez celles qui effectuent le plus de travail.

    ![Liste des fonctions d’utilisation de l’UC des outils de diagnostic](../profiling/media/diag-tools-cpu-usage-function-list.png "DiagToolsCPUUsageFunctionList")

    > [!TIP]
    > Les fonctions sont classées par ordre et ce sont celles qui effectuent le plus de travail qui figurent en haut de la liste (elles ne sont pas classées selon leur ordre d’appel). Ainsi, vous pouvez identifier rapidement les fonctions avec les temps d’exécution les plus longs.

2. Dans la liste, double-cliquez sur l’une des fonctions d’application qui effectuent le plus de travail.

    Lorsque vous double-cliquez sur une fonction, la vue **Appelant/appelé** s’ouvre dans le volet gauche.

    ![Outils de diagnostic - Vue Appelant/appelé](../profiling/media/diag-tools-caller-callee.png "DiagToolsCallerCallee")

    Dans cette vue, la fonction sélectionnée apparaît dans le titre et dans la zone **Fonction active** (ici, GetNumber). La fonction qui a appelé la fonction active s’affiche sur la gauche sous **Fonctions appelantes**, et toutes les fonctions appelées par la fonction active s’affichent dans la zone **Fonctions appelées** sur la droite. Vous pouvez sélectionner l’une ou l’autre de ces zones pour modifier la fonction active.

    Cette vue montre la durée totale (en ms), ainsi que le pourcentage du temps global d’exécution de l’application, nécessaires à l’exécution de la fonction.
    La section **Corps de la fonction** montre également la durée totale (et le pourcentage correspondant) passée dans le corps de la fonction, à l’exclusion du temps passé dans les fonctions appelantes et appelées. (Dans cet exemple, 2367 ms sur 2389 ont été passées dans le corps de la fonction. Les 22 ms restantes ont été passées dans le code externe appelé par cette fonction.)

    > [!TIP]
    > Des valeurs élevées dans le **corps de la fonction** peuvent indiquer un goulot d’étranglement de performances au sein de la fonction.

3. Pour voir l’ordre d’appel des fonctions, sélectionnez **Arborescence des appels** dans la liste déroulante située en haut du volet.

    Chaque zone numérotée dans l'illustration est en rapport avec une étape de la procédure.

    ::: moniker range=">=vs-2019"
    ![Arborescence des appels des outils de diagnostic](../profiling/media/vs-2019/diag-tools-call-tree.png "DiagToolsCallTree")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Arborescence des appels des outils de diagnostic](../profiling/media/diag-tools-call-tree.png "DiagToolsCallTree")
    ::: moniker-end

    |Image|Description|
    |-|-|
    |![Étape 1](../profiling/media/ProcGuid_1.png "ProcGuid_1")|Le nœud de premier niveau des arborescences d'appels de l'outil Utilisation de l'UC est un pseudo-nœud|
    |![Étape 2](../profiling/media/ProcGuid_2.png "ProcGuid_2")|Dans la plupart des applications, quand l'option [Afficher le code externe](#view-external-code) est désactivée, le nœud de deuxième niveau est un nœud **[Code externe]** contenant le code système et de l'infrastructure qui démarre et arrête l'application, dessine l'interface utilisateur, contrôle la planification des threads et fournit d'autres services de niveau inférieur à l'application.|
    |![Étape 3](../profiling/media/ProcGuid_3.png "ProcGuid_3")|Les enfants du nœud de deuxième niveau sont les méthodes en code utilisateur et des routines asynchrones appelées ou créées par le code système et d'infrastructure de deuxième niveau.|
    |![Étape 4](../profiling/media/ProcGuid_4.png "ProcGuid_4")|Les nœuds enfants d'une méthode contiennent des données seulement pour les appels de la méthode parente. Lorsque l'option **Afficher le Code externe** est désactivée, les méthodes d'application peuvent également contenir un nœud **[Code externe]** .|

    Voici davantage d’informations sur les valeurs de colonne :

    - La section **Total UC (ms)** montre la quantité de travail effectué par la fonction et toute autre fonction qu’elle a appelée. Les valeurs d’UC total élevées indiquent les fonctions les plus coûteuses.

    - La colonne **Processeur auto (ms)** indique la quantité de travail effectué par le code dans le corps de la fonction, à l’exception du travail effectué par les fonctions qu’elle a appelées. Des valeurs élevées dans la colonne **Processeur auto (ms)** peuvent indiquer un goulot d’étranglement des performances au sein de la fonction.

    - **Modules** Nom du module contenant la fonction, ou nombre de modules contenant les fonctions dans un nœud [Code externe].

    ::: moniker range=">=vs-2019"
    Pour afficher les appels de fonction qui présentent la plus grande consommation du processeur dans l’arborescence des appels, cliquez sur **Développer le chemin réactif**.

    ![Chemin réactif des outils de diagnostic](../profiling/media/vs-2019/diag-tools-hot-path.png "DiagToolsHotPath")
    ::: moniker-end

    > [!NOTE]
    > Si vous voyez du code dans l’arborescence des appels marqués comme du code « interrompu » ou « pile intraitable », cela signifie que les événements de suivi d’événements pour Windows (ETW) ont probablement été supprimés. Essayez de collecter la même trace une deuxième fois pour résoudre le problème.

## <a name="view-external-code"></a>Afficher le code externe

Le code externe correspond aux fonctions des composants système et de framework exécutés par le code que vous écrivez. Le code externe inclut les fonctions qui démarrent et arrêtent l'application, dessinent l'interface utilisateur, contrôlent les threads et fournissent d'autres services de bas niveau à l'application. Dans la plupart des cas, vous n’êtes pas intéressé par le code externe. l’outil utilisation de l’UC regroupe donc les fonctions externes d’une méthode utilisateur en un seul nœud **[code externe]** .

Si vous voulez afficher les chemins d’appel du code externe, choisissez **Afficher le code externe** dans la liste **Filtrer la vue**, puis **Appliquer**.

![Choisir Filtrer l'affichage, puis Afficher le code externe](../profiling/media/diag-tools-show-external-code.png "DiagToolsShowExternalCode")

N'oubliez pas que de nombreuses chaînes d'appel en code externe sont profondément imbriquées, la largeur de la colonne Nom de fonction ne peut pas dépasser la largeur d'affichage de presque tous les moniteurs d'ordinateur, sauf les plus larges. Dans ce cas, les noms de fonction sont affichés sous la forme **[...]**.

Utilisez la zone de recherche pour trouver le nœud que vous cherchez, puis utilisez la barre de défilement horizontal pour afficher les données dans la vue.

> [!TIP]
> Si vous profilez du code externe qui appelle des fonctions Windows, vous devez vérifier que vous disposez des fichiers .*pdb* les plus récents. Sans ces fichiers, vos vues de rapports répertorient des noms de fonctions Windows cryptés et difficiles à comprendre. Pour plus d’informations sur la façon de s’assurer que vous disposez des fichiers dont vous avez besoin, consultez [spécifier les fichiers de symboles (. pdb) et les fichiers sources dans le débogueur](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris comment collecter et analyser les données d’utilisation de l’UC. Si vous avez déjà [découvert les outils de profilage](../profiling/profiling-feature-tour.md), vous pouvez souhaiter avoir une vue d’ensemble rapide de la manière d’analyser l’utilisation de la mémoire dans vos applications.

> [!div class="nextstepaction"]
> [Profiler l’utilisation de la mémoire dans Visual Studio](../profiling/memory-usage.md)
