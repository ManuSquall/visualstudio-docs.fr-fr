---
title: Prise en main des outils de profilage
description: Examinez brièvement les différents outils de diagnostic disponibles dans Visual Studio.
ms.custom: ''
ms.date: 02/18/2021
ms.topic: overview
f1_keywords:
- vs.diagnosticshub.overview
dev_langs:
- CSharp
helpviewer_keywords:
- diagnostic tools
ms.assetid: d2ee0301-ea78-43d8-851a-71b7b2043d73
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b5fb35c1cd30f872d2a58504f73596357cc60025
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729323"
---
# <a name="first-look-at-profiling-tools"></a>Découvrir les outils de profilage

Visual Studio propose des outils de profilage pour vous aider à diagnostiquer différents types de problèmes de performances en fonction de votre type d’application. Dans cet article, nous présentons rapidement les outils de profilage les plus courants.

Pour voir la prise en charge des outils de profilage pour différents types d’applications, consultez [quel outil dois-je utiliser ?](#which-tool-should-i-use)

## <a name="measure-performance-while-debugging"></a>Mesurer les performances pendant le débogage

Les outils de profilage auxquels vous avez accès pendant une session de débogage sont disponibles dans la fenêtre Outils de diagnostic. Cette fenêtre apparaît automatiquement, sauf si vous l’avez désactivée. Pour afficher la fenêtre, cliquez sur **Déboguer/fenêtres/afficher le outils de diagnostic** (ou appuyez sur **CTRL**  +  **ALT**  +  **F2**). Une fois la fenêtre ouverte, vous pouvez sélectionner les outils dont vous souhaitez collecter les données.

![Fenêtre Outils de diagnostic](../profiling/media/prof-tour-diagnostic-tools.png "Outils de diagnostic")

Pendant le débogage, vous pouvez utiliser la fenêtre **Outils de diagnostic** pour analyser l’utilisation du processeur et de la mémoire, et vous pouvez voir des événements indiquant des informations sur les performances.

![Vue Résumé de la Outils de diagnostic](../profiling/media/prof-tour-cpu-and-memory-graph.gif "Résumé de la Outils de diagnostic")

La fenêtre de **outils de diagnostic** est une méthode courante pour profiler des applications, mais pour les builds de version, vous pouvez également effectuer une analyse de votre application à la place. Pour plus d’informations sur les différentes approches, consultez [exécuter les outils de profilage avec ou sans le débogueur](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Pour voir la prise en charge des outils de profilage pour différents types d’applications, consultez [quel outil dois-je utiliser ?](#which-tool-should-i-use)

Les outils disponibles dans la fenêtre de Outils de diagnostic ou au cours d’une session de débogage sont les suivants :
- [Utilisation de l’UC](../profiling/beginners-guide-to-performance-profiling.md)
- [Utilisation de la mémoire](../profiling/memory-usage.md)
- [Conseils sur les performances](../profiling/perftips.md)

> [!NOTE]
> Windows 8 et les versions ultérieures sont nécessaires pour exécuter les Outils de profilage avec le débogueur (fenêtre **Outils de diagnostic**). Vous pouvez utiliser les outils d' [autopsie](#post_mortem) avec Windows 7 et versions ultérieures. 

## <a name="measure-performance-in-release-builds"></a><a name="post_mortem"></a> Mesurer les performances dans les versions release

Les outils du profileur de performances sont conçus pour fournir une analyse des versions **Release** . Dans le profileur de performances, vous pouvez collecter des informations de diagnostic pendant que l’application est en cours d’exécution, puis examiner les informations collectées après l’arrêt de l’application (une analyse postale).

Ouvrez le profileur de performances en choisissant **Déboguer** le  >  **profileur de performances** (ou **ALT + F2**).

![Profileur de performances](../profiling/media/prof-tour-performance-profiler.png "Profileur de performances")

Pour plus d’informations sur l’utilisation de l’outil utilisation de l’UC ou utilisation de la mémoire dans le profileur de performances et les outils intégrés au débogueur, consultez [exécuter les outils de profilage avec ou sans le débogueur](../profiling/running-profiling-tools-with-or-without-the-debugger.md). 

Les outils disponibles dans le profileur de performances sont les suivants :

- [Utilisation de l’UC](../profiling/cpu-usage.md)
- [Allocation d’objets .NET](../profiling/dotnet-alloc-tool.md)
- [Utilisation de la mémoire](../profiling/memory-usage-without-debugging2.md)
- [Outil .NET Async](../profiling/analyze-async.md)
- [Outil de base de données](../profiling/analyze-database.md)
- [Utilisation du GPU](../profiling/gpu-usage.md)

Pour voir la prise en charge des outils de profilage pour différents types d’applications, consultez [quel outil dois-je utiliser ?](#which-tool-should-i-use)

Dans certains scénarios, la fenêtre vous permet de sélectionner [plusieurs outils de profilage](../profiling/use-multiple-profiler-tools-simultaneously.md). Les outils comme Utilisation de l’UC peuvent fournir des données complémentaires que vous pouvez utiliser dans votre analyse. Vous pouvez également utiliser le [profileur de ligne de commande](../profiling/profile-apps-from-command-line.md) pour activer des scénarios impliquant plusieurs outils de profilage.

## <a name="examine-performance-using-perftips"></a>Examiner les performances à l’aide de PerfTips

Souvent, le moyen le plus simple d’afficher les informations de performances consiste à utiliser [PerfTips](../profiling/perftips.md). À l’aide de PerfTips, vous pouvez afficher des informations sur les performances lors de l’interaction avec votre code. Vous pouvez consulter des informations telles que la durée de l’événement (mesurée à partir de la dernière suspension du débogueur ou du démarrage de l’application). Par exemple, si vous parcourez le code pas à pas (F10, F11), PerfTips affiche la durée d’exécution de l’application de l’opération précédente à l’étape actuelle.

![Profilage de la visite guidée PerfTips](../profiling/media/prof-tour-perf-tips.png "Profilage de la visite guidée PerfTips")

Vous pouvez utiliser PerfTips pour examiner le temps nécessaire à l’exécution d’un bloc de code ou le temps nécessaire à la réalisation d’une seule fonction.

PerfTips affiche les événements qui apparaissent également dans la vue **événements** du outils de diagnostic. Dans la vue **événements** , vous pouvez afficher différents événements qui se produisent pendant le débogage, tels que le paramètre d’un point d’arrêt ou une opération de pas à pas de code.

![Affichage des événements de Outils de diagnostic](../profiling/media/prof-tour-events.png "Événements d’affichage Outils de diagnostic")

 > [!NOTE]
 > Si vous avez Visual Studio Enterprise, vous pouvez également voir [Événements IntelliTrace](../debugger/intellitrace.md) sous cet onglet.

## <a name="analyze-cpu-usage"></a>Analyser l’utilisation de l’UC

L’outil Utilisation de l’UC est un bon point de départ pour analyser les performances de votre application. Il vous en dit plus sur les ressources du processeur qu’utilise votre application. Vous pouvez utiliser l' [outil utilisation de l’UC intégré au débogueur](../profiling/beginners-guide-to-performance-profiling.md) ou l' [outil d’utilisation](../profiling/cpu-usage.md)de l’UC.

Lorsque vous utilisez l’outil de l’utilisation de l’UC intégré au débogueur, ouvrez la fenêtre de l’outil de diagnostic (si elle est fermée, choisissez **Déboguer/fenêtres/afficher les outils de diagnostic**). Pendant le débogage, ouvrez la vue  **Résumé** , puis sélectionnez **enregistrer le profil** de l’UC.

![Activer l’utilisation de l’UC dans le Outils de diagnostic](../profiling/media/prof-tour-enable-cpu-profiling.png "Outils de diagnostic activer l’utilisation de l’UC")

Une façon d’utiliser l’outil consiste à définir deux points d’arrêt dans votre code, l’un au début et l’autre à la fin de la fonction ou la région de code que vous souhaitez analyser. Examinez les données de profilage quand une pause est marquée au second point d’arrêt.

La vue **Utilisation de l’UC** affiche une liste de fonctions, classées par durée d’exécution décroissante. Cette liste vous permet de repérer les fonctions dans lesquelles se produisent des goulots d’étranglement.

![Affichage de l’utilisation de l’UC Outils de diagnostic](../profiling/media/prof-tour-cpu-usage.png "Utilisation du processeur Outils de diagnostic")

Double-cliquez sur une fonction digne d’intérêt ; apparaît alors une vue « papillon » plus détaillée composée de trois volets, indiquant la fonction sélectionnée (au milieu), la fonction appelante (à gauche) et les fonctions appelées (à droite). La section **Corps de la fonction** montre la durée totale (et le pourcentage correspondant) passée dans le corps de la fonction, à l’exclusion du temps passé dans les fonctions appelantes et appelées. Ces données peuvent vous aider à déterminer si la fonction elle-même est un goulot d’étranglement.

![Vue « papillon » de l’appelé Outils de diagnostic appelant](../profiling/media/prof-tour-cpu-usage-caller-callee.png "Vue de l’appelé Outils de diagnostic appelant")

## <a name="analyze-memory-usage"></a>Analyser l’utilisation de la mémoire

La fenêtre **outils de diagnostic** vous permet également d’évaluer l’utilisation de la mémoire dans votre application à l’aide de l’outil utilisation de la **mémoire** . Par exemple, vous pouvez consulter le nombre et la taille des objets sur le tas. Vous pouvez utiliser l' [outil utilisation de la mémoire intégrée au débogueur](../profiling/memory-usage.md) ou l' [outil utilisation](../profiling/memory-usage-without-debugging2.md) de la mémoire de l’autopsie dans le profileur de performances.

Les développeurs .NET peuvent choisir entre l' [outil d’allocation d’objets .net](../profiling/dotnet-alloc-tool.md) ou l’outil utilisation de la [mémoire](../profiling/memory-usage.md) .

- L’outil d' **allocation d’objets .net** vous aide à identifier les modèles d’allocation et les anomalies dans votre code .net, et vous aide à identifier les problèmes courants avec garbage collection. Cet outil s’exécute uniquement comme un outil d’autopsie. Vous pouvez exécuter cet outil sur des ordinateurs locaux ou distants.
- L’outil utilisation de la **mémoire** est utile pour identifier les fuites de mémoire, qui ne sont généralement pas courantes dans les applications .net. Si vous devez utiliser les fonctionnalités du débogueur lors de la vérification de la mémoire, telles que l’exécution pas à pas du code, l’outil d' [utilisation de la mémoire intégré au débogueur](../profiling/beginners-guide-to-performance-profiling.md) est recommandé.

Pour analyser l’utilisation de la mémoire avec l’outil utilisation de la **mémoire** , vous devez prendre au moins un instantané de la mémoire. Souvent, la meilleure façon d’analyser la mémoire consiste à prendre deux instantanés, le premier juste avant un problème de mémoire suspecté et le second juste après. Ensuite, vous pouvez visualiser une comparaison des deux instantanés et voir exactement ce qui a changé. L’illustration suivante montre l’utilisation d’un instantané avec l’outil intégré au débogueur.

![Prendre un instantané dans le Outils de diagnostic](../profiling/media/prof-tour-take-snapshots.gif "Outils de diagnostic prendre des captures instantanées")

Lorsque vous sélectionnez l’un des liens de direction, vous recevez une vue différentielle du tas (une ![augmentation de l’utilisation](../profiling/media/prof-tour-mem-usage-up-arrow.png "Augmentation de l’utilisation de la mémoire") de la mémoire rouge pour les flèches affiche un nombre croissant d’objets (à gauche) ou une taille de segment de mémoire plus grande (à droite)). Si vous cliquez sur le lien de droite, vous obtenez une vue de tas différentielle qui indique en premier les objets dont la taille a augmenté le plus dans le tas. Cela peut vous aider à identifier les problèmes de mémoire. Par exemple, dans l’illustration ci-dessous, les octets utilisés par les objets `ClassHandlersStore` ont augmenté de 3 492 unités dans le deuxième instantané.

![Vue diff du tas Outils de diagnostic](../profiling/media/prof-tour-mem-usage-diff-heap.png "Vue diff du tas Outils de diagnostic")

Par contre, si vous cliquez sur le lien sur la gauche dans la vue **Utilisation de la mémoire**, la vue du tas est organisée par nombre d’objets ; les objets d’un type particulier dont le nombre a le plus augmenté sont affichés en haut (en fonction de la colonne **Différence de nombre**).

## <a name="analyze-resource-consumption-xaml"></a>Analyser la consommation des ressources (XAML)

Dans les applications XAML, comme les applications WPF pour poste de travail Windows et les applications UWP, vous pouvez analyser la consommation des ressources avec l’outil Chronologie de l’application. Par exemple, vous pouvez analyser le temps passé par votre application à préparer les trames de l’interface utilisateur (mise en page et rendu), à traiter les demandes du réseau et des disques, et dans les scénarios comme le démarrage de l’application, le chargement des pages et le redimensionnement des fenêtres. Pour utiliser l’outil, choisissez **Chronologie de l’application** dans le profileur de performances, puis choisissez **Démarrer**. Dans votre application, effectuez le scénario susceptible de présenter un problème de consommation de ressources, puis choisissez **Arrêter la collecte** pour générer le rapport.

La présence de taux de trames faibles dans le graphique **Débit visuel** peut correspondre à des problèmes visuels que vous constatez quand vous exécutez votre application. De même, la présence de nombres élevés dans le graphique **Utilisation du thread d’interface utilisateur** peut également indiquer des problèmes de réactivité de l’interface utilisateur. Dans le rapport, vous pouvez sélectionner une période de temps susceptible de présenter un problème de performances, puis examiner les activités de thread de l’interface utilisateur détaillées dans la vue Détails de la chronologie (volet inférieur).

![Outil de profilage chronologie de l’application](../profiling/media/prof-tour-application-timeline.gif "chronologie de l’application de la visite guidée du profilage")

Dans la vue Détails de la chronologie, vous pouvez trouver des informations telles que le type d’activité (ou l’élément d’interface utilisateur impliqué), ainsi que la durée de l’activité. Par exemple, dans l’illustration, un événement **Layout** (disposition) pour un contrôle de grille prend 57,53 ms.

Pour plus d’informations, consultez [Chronologie de l’application](../profiling/application-timeline.md).

::: moniker range=">=vs-2019"

## <a name="examine-application-events"></a>Examiner les événements d’application

L' [Observateur d’événements](../profiling/events-viewer.md) génériques vous permet d’afficher l’activité de votre application via une liste d’événements, tels que le chargement de module, le démarrage de thread et les configurations système, afin de mieux diagnostiquer le fonctionnement de votre application dans le profileur Visual Studio. Cet outil est disponible dans le profileur de performances. Ouvrez le profileur de performances en choisissant **Déboguer** le  >  **profileur de performances** (ou **ALT + F2**).

L’outil affiche chaque événement dans un affichage de liste. Les colonnes fournissent des informations sur chaque événement, telles que le nom de l’événement, l’horodatage et l’ID du processus.

![Trace de observateur d’événements](../profiling/media/eventviewertrace.png "Trace de observateur d’événements")

## <a name="analyze-asynchronous-code-net"></a>Analyser le code asynchrone (.NET)

L' [outil .net Async](../profiling/analyze-async.md) vous permet d’analyser les performances du code asynchrone dans votre application. Cet outil est disponible dans le profileur de performances. Ouvrez le profileur de performances en choisissant **Déboguer** le  >  **profileur de performances** (ou **ALT + F2**).

L’outil affiche chaque opération asynchrone dans un affichage de liste. Vous pouvez voir des informations telles que l’heure de début, l’heure de fin et la durée totale d’une opération asynchrone.

![L’outil .NET Async s’est arrêté](../profiling/media/async-tool-opened.png "L’outil .NET Async s’est arrêté")

## <a name="analyze-database-performance-net-core"></a>Analyser les performances d’une base de données (.NET Core)

Pour les applications .NET Core qui utilisent ADO.NET ou Entity Framework Core, l' [outil de base de données](../profiling/analyze-database.md) vous permet d’enregistrer les requêtes de base de données que votre application effectue pendant une session de diagnostic. Vous pouvez ensuite analyser des informations sur des requêtes individuelles afin de trouver les endroits où les performances de votre application peuvent être améliorées. Cet outil est disponible dans le profileur de performances. Ouvrez le profileur de performances en choisissant **Déboguer** le  >  **profileur de performances** (ou **ALT + F2**).

L’outil affiche chaque requête dans un affichage de liste. Vous pouvez voir des informations telles que l’heure de début et la durée de la requête.

![Louer](./media/db-gotosource.png "Allocation")

## <a name="visualize-net-counters-net-core"></a>Visualiser les compteurs .NET (.NET Core)

À compter de Visual Studio 2019 version 16,7, vous pouvez utiliser l' [outil compteurs .net](../profiling/dotnet-counters-tool.md) dans Visual Studio pour visualiser les compteurs de performances. Vous pouvez visualiser les compteurs créés à l’aide des [compteurs dotnet](/dotnet/core/diagnostics/dotnet-counters). les compteurs dotnet prennent en charge de nombreux compteurs tels que l’utilisation de l’UC et la taille du tas du garbage collector.

L’outil affiche des valeurs dynamiques pour chaque compteur dans une vue liste.

:::image type="content" source="../profiling/media/dotnet-counters-tool-collecting.png" alt-text="Collecte de l’outil de compteur .NET.":::

::: moniker-end

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>Examiner les événements d’accessibilité et de performances de l’IU (UWP)

Dans vos applications UWP, vous pouvez activer l’analyse de l' **interface utilisateur** dans la fenêtre **outils de diagnostic** . L’outil recherche les problèmes de performances ou d’accessibilité et les affiche dans la vue **Événements** pendant le débogage. Les descriptions des événements fournissent des informations qui peuvent aider à résoudre les problèmes.

![Afficher les événements d’analyse de l’interface utilisateur dans les outils de diagnostic](../profiling/media/prof-tour-ui-analysis.png "Outils de diagnostic afficher les événements d’analyse de l’interface utilisateur")

## <a name="analyze-gpu-usage-direct3d"></a>Analyser l’utilisation du GPU (Direct3D)

Dans les applications Direct3D (les composants Direct3D doivent être en C++), vous pouvez examiner l’activité sur le GPU et analyser les problèmes de performances. Pour plus d’informations, consultez [Utilisation du GPU](./gpu-usage.md). Pour utiliser l’outil, choisissez **Utilisation du GPU** dans le profileur de performances, puis choisissez **Démarrer**. Dans votre application, effectuez le scénario à profiler, puis choisissez **Arrêter la collecte** pour générer un rapport.

Quand vous sélectionnez une période de temps dans les graphiques et que vous choisissez **Afficher les détails**, une vue détaillée s’affiche dans le volet inférieur. Dans la vue détaillée, vous pouvez consulter le volume d’activité qui se produit sur chaque UC et GPU. Sélectionnez les événements dans le volet inférieur pour afficher des fenêtres contextuelles dans la chronologie. Par exemple, sélectionnez l’événement **Présent** pour afficher les fenêtres contextuelles des appels **Présent**. (Les lignes VSync verticales gris clair peuvent être utilisées comme référence pour déterminer si certains appels **présents** ont manqué Vsync. Il doit y avoir un seul appel **présent** entre chaque VSyncs pour que l’application atteigne régulièrement 60 fps.)

![Outil de profilage de l’utilisation du GPU](../profiling/media/prof-tour-gpu-usage.png "Utilisation du GPU diag")

Vous pouvez également utiliser les graphiques pour déterminer la présence éventuelle de goulots d’étranglement liés à l’UC ou au GPU.

::: moniker range="vs-2017"
## <a name="analyze-performance-javascript-uwp"></a>Analyser les performances (JavaScript UWP)

Pour les applications UWP, vous pouvez utiliser les outils Mémoire JavaScript et Réactivité de l’interface utilisateur HTML.

L’outil Mémoire JavaScript est similaire à l’outil Utilisation de la mémoire disponible pour les autres types d’application. Vous pouvez utiliser cet outil pour comprendre l’utilisation de la mémoire et rechercher les fuites de mémoire dans votre application. Pour plus d’informations sur l’outil, consultez [Mémoire JavaScript](../profiling/javascript-memory.md).

![Outil de profilage de mémoire JavaScript](../profiling/media/diagjsmemory.png "Diagnostics")

Pour diagnostiquer la réactivité de l’interface utilisateur, la lenteur du temps de chargement et la lenteur des mises à jour visuelles dans les applications UWP, utilisez l’outil Réactivité de l’interface utilisateur HTML. L’utilisation est similaire à l’outil Chronologie de l’application pour les autres types d’application. Pour plus d’informations, consultez [Réactivité de l’interface utilisateur HTML](../profiling/html-ui-responsiveness.md).

![Outil de profilage de réactivité de l’interface utilisateur HTML](../profiling/media/diaghtmlresp.png "Réactivité")
::: moniker-end

::: moniker range="vs-2017"
## <a name="analyze-network-usage-uwp"></a>Analyser l’utilisation du réseau (UWP)

Dans les applications UWP, vous pouvez analyser les opérations réseau effectuées à l’aide de l' `Windows.Web.Http` API. Cet outil peut vous aider à résoudre des problèmes tels que les problèmes d’accès et d’authentification, l’utilisation incorrecte du cache et les performances d’affichage et de téléchargement médiocres. Pour utiliser l’outil, choisissez **Réseau** dans le profileur de performances, puis choisissez **Démarrer**. Dans votre application, effectuez le scénario qui utilise `Windows.Web.Http`, puis choisissez **Arrêter la collecte** pour générer le rapport.

![Outil de profilage de l’utilisation du réseau](../profiling/media/prof-tour-network-usage.png "Utilisation du réseau de diagnostic")

Sélectionnez une opération dans la vue du résumé pour afficher des informations plus détaillées.

![Informations détaillées dans l’outil utilisation du réseau](../profiling/media/prof-tour-network-usage-details.png "Détails de l’utilisation du réseau diag")

Pour plus d’informations, consultez [Utilisation du réseau](../profiling/network-usage.md).
::: moniker-end

## <a name="analyze-performance-legacy-tools"></a>Analyser les performances (outils hérités)

::: moniker range="vs-2017"
Si vous avez besoin de fonctionnalités qui ne sont pas présentes dans les outils Utilisation de l’UC ou Utilisation de la mémoire, telles que l’instrumentation, et que vous exécutez des applications de bureau ou ASP.NET, vous pouvez utiliser l’Explorateur de performances pour le profilage. (Non pris en charge dans les applications UWP). Pour plus d’informations, consultez [Explorateur de performances](../profiling/performance-explorer.md).
::: moniker-end

::: moniker range=">=vs-2019"
Dans Visual Studio 2019, les Explorateur de performances héritées et les outils de profilage associés tels que l’Assistant Performance ont été repliés dans le profileur de performances, que vous pouvez ouvrir à l’aide de **Debug**  >  **performance Profiler**. Dans le profileur de performances, les outils de diagnostic disponibles dépendent de la cible choisie et du projet de démarrage actuel ouvert. L’outil utilisation de l’UC fournit la fonctionnalité d’échantillonnage précédemment prise en charge dans l’Assistant performance. L’outil d’instrumentation fournit la fonctionnalité de profilage instrumenté (pour les nombres d’appels et les durées précis) qui étaient dans l’Assistant performance. Des outils mémoire supplémentaires s’affichent également dans le profileur de performances.
::: moniker-end

![Outil Explorateur de performances](../profiling/media/prof-tour-performance-explorer.png "Explorateur de performances")

## <a name="which-tool-should-i-use"></a>Quel outil dois-je utiliser ?

Voici un tableau qui recense les différents outils proposés par Visual Studio, ainsi que les différents types de projet avec lesquels vous pouvez les utiliser :

::: moniker range=">=vs-2019"
|Outil d’analyse des performances|Ordinateurs Windows|UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[Conseils sur les performances](../profiling/perftips.md)|Oui|Oui|Oui|
|[Utilisation du processeur](../profiling/beginners-guide-to-performance-profiling.md)|Oui|Oui|Oui|
|[Utilisation de la mémoire](../profiling/memory-usage.md)|Oui|Oui|Oui|
|[Allocation d’objets .NET](../profiling/dotnet-alloc-tool.md)|Oui (.NET uniquement)|Oui|Oui|
|[Utilisation du GPU](./gpu-usage.md)|Oui|Oui|non|
|[Chronologie de l'application](../profiling/application-timeline.md)|Oui (XAML)|Oui|non|
|[Observateur d’événements](../profiling/events-viewer.md)|Oui|Oui|Oui|
|[.NET Async](../profiling/analyze-async.md)|Oui (.NET uniquement)|Oui|Oui|
|[.NET Counters](../profiling/dotnet-counters-tool.md)|Oui (.NET Core uniquement)|non|Oui (ASP.NET Core uniquement)|
|[Sauvegarde de la base de données](../profiling/analyze-database.md)|Oui (.NET Core uniquement)|non|Oui (ASP.NET Core uniquement)|
|[Explorateur de performances](#analyze-performance-legacy-tools)|non|non|non|
|[IntelliTrace](../debugger/intellitrace.md)|.NET avec Visual Studio Enterprise uniquement|.NET avec Visual Studio Enterprise uniquement|.NET avec Visual Studio Enterprise uniquement|
::: moniker-end

::: moniker range="vs-2017"
|Outil d’analyse des performances|Ordinateurs Windows|UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[Utilisation du processeur](../profiling/beginners-guide-to-performance-profiling.md)|Oui|Oui|Oui|
|[Utilisation de la mémoire](../profiling/memory-usage.md)|Oui|Oui|Oui|
|[Utilisation du GPU](./gpu-usage.md)|Oui|Oui|non|
|[Chronologie de l'application](../profiling/application-timeline.md)|Oui (XAML)|Oui|non|
|[Conseils sur les performances](../profiling/perftips.md)|Oui|oui pour XAML, non pour HTML|Oui|
|[Explorateur de performances](../profiling/performance-explorer.md)|Oui|non|Oui|
|[IntelliTrace](../debugger/intellitrace.md)|.NET avec Visual Studio Enterprise uniquement|.NET avec Visual Studio Enterprise uniquement|.NET avec Visual Studio Enterprise uniquement|
|[Utilisation du réseau](../profiling/network-usage.md)|non|Oui|non|
|[Réactivité de l’interface utilisateur HTML](../profiling/html-ui-responsiveness.md)|non|oui pour HTML, non pour XAML|non|
|[Mémoire JavaScript](../profiling/javascript-memory.md)|non|oui pour HTML, non pour XAML|non|
::: moniker-end


## <a name="see-also"></a>Voir aussi
- [Débogage dans Visual Studio](../debugger/debugger-feature-tour.md)