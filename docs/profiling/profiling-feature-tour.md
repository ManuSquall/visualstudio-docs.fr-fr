---
title: "Visite guidée des fonctionnalités de profilage | Microsoft Docs"
ms.custom: 
ms.date: 02/03/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugger
ms.assetid: d2ee0301-ea78-43d8-851a-71b7b2043d73
caps.latest.revision: 1
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
ms.sourcegitcommit: 2beee9df6c4897d1fa7d55502a7ed277a1eb6046
ms.openlocfilehash: 4a64d7385009b6d502fc20acfbead4b49323fa4f
ms.lasthandoff: 03/21/2017

---
# <a name="profiling-feature-tour"></a>Visite guidée des fonctionnalités de profilage

Visual Studio propose des outils de profilage pour vous aider à diagnostiquer différents types de problèmes de performances en fonction de votre type d’application.

Les outils de profilage auxquels vous avez accès pendant une session de débogage sont disponibles dans la fenêtre Outils de diagnostic. Cette fenêtre apparaît automatiquement, sauf si vous l’avez désactivée. Pour afficher la fenêtre, cliquez sur **Déboguer / Fenêtres / Afficher les outils de diagnostic**. Une fois la fenêtre ouverte, vous pouvez sélectionner les outils dont vous souhaitez collecter les données.

![Fenêtre Outils de diagnostic](../profiling/media/prof-tour-diagnostic-tools.png "Outils de diagnostic")

Pendant le débogage, vous pouvez utiliser la fenêtre **Outils de diagnostic** pour analyser l’utilisation du processeur et de la mémoire, et vous pouvez voir des événements indiquant des informations sur les performances.

![Vue Résumé des outils de diagnostic](../profiling/media/prof-tour-cpu-and-memory-graph.gif "Résumé des outils de diagnostic")

La fenêtre **Outils de diagnostic** est souvent la meilleure méthode pour profiler des applications, mais vous pouvez également effectuer une analyse post-mortem de votre application à la place. Pour plus d’informations sur les différentes approches, consultez [Exécution des outils de profilage avec ou sans le débogueur](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="analyze-cpu-usage"></a>Analyser l'utilisation de l'UC

L’outil Utilisation de l’UC est un bon point de départ pour analyser les performances de votre application. Il vous en dit plus sur les ressources du processeur qu’utilise votre application. Pour obtenir une description plus détaillée de l’outil Utilisation de l’UC, consultez [Guide du débutant en profilage des performances](../profiling/beginners-guide-to-performance-profiling.md).

Dans la vue **Résumé** des outils de diagnostic, choisissez **Activer le profilage de l’UC** (vous devez être dans une session de débogage).

![Activer l’utilisation de l’UC dans les Outils de diagnostic](../profiling/media/prof-tour-enable-cpu-profiling.png "Outils de diagnostic - Activer l’utilisation de l’UC")

Pour utiliser l’outil plus efficacement, définissez deux points d’arrêt dans votre code, un au début et un à la fin de la fonction ou de la région de code que vous souhaitez analyser. Examinez les données de profilage quand une pause est marquée au second point d’arrêt.

La vue **Utilisation de l’UC** affiche une liste de fonctions, classées par durée d’exécution décroissante. Cette liste vous permet de repérer les fonctions dans lesquelles se produisent des goulots d’étranglement.

![Vue Utilisation de l’UC dans les Outils de diagnostic](../profiling/media/prof-tour-cpu-usage.png "Utilisation de l’UC dans les Outils de diagnostic")

Double-cliquez sur une fonction digne d’intérêt ; apparaît alors une vue « papillon » plus détaillée composée de trois volets, indiquant la fonction sélectionnée (au milieu), la fonction appelante (à gauche) et les fonctions appelées (à droite). La section **Corps de la fonction** montre la durée totale (et le pourcentage correspondant) passée dans le corps de la fonction, à l’exclusion du temps passé dans les fonctions appelantes et appelées. Ces données peuvent vous aider à déterminer si la fonction elle-même est un goulot d’étranglement.

![Vue « papillon » fonctions appelantes/fonctions appelées dans les Outils de diagnostic](../profiling/media/prof-tour-cpu-usage-caller-callee.png "Vue fonctions appelantes/fonctions appelées dans les Outils de diagnostic")

## <a name="analyze-memory-usage"></a>Analyser l’utilisation de la mémoire

La fenêtre Outils de diagnostic vous permet également d’évaluer l’utilisation de la mémoire dans votre application. Par exemple, vous pouvez consulter le nombre et la taille des objets sur le tas. Pour plus d’instructions sur l’analyse de la mémoire, consultez [Utilisation de la mémoire](../profiling/memory-usage.md).

Pour analyser l’utilisation de la mémoire, vous devez prendre au moins un instantané de la mémoire pendant le débogage. Souvent, la meilleure façon d’analyser la mémoire consiste à prendre deux instantanés, le premier juste avant un problème de mémoire suspecté et le second juste après. Ensuite, vous pouvez visualiser une comparaison des deux instantanés et voir exactement ce qui a changé.

![Prendre un instantané dans les Outils de diagnostic](../profiling/media/prof-tour-take-snapshots.gif "Outils de diagnostic - Prendre un instantané")

Quand vous sélectionnez un des liens associés à une flèche, vous obtenez une vue différentielle du tas (une flèche rouge vers le haut ![Augmentation de l’utilisation de la mémoire](../profiling/media/prof-tour-mem-usage-up-arrow.png "Augmentation de l’utilisation de la mémoire") indique un nombre d’objets croissant (à gauche) ou une taille de tas croissante (à droite)). Si vous cliquez sur le lien de droite, vous obtenez une vue de tas différentielle qui indique en premier les objets dont la taille a augmenté le plus dans le tas. Cela peut vous aider à identifier les problèmes de mémoire. Par exemple, dans l’illustration ci-dessous, les octets utilisés par les objets `ClassHandlersStore` ont augmenté de 3 492 unités dans le deuxième instantané.

![Vue comparative du tas dans les Outils de diagnostic](../profiling/media/prof-tour-mem-usage-diff-heap.png "Vue comparative du tas dans les Outils de diagnostic")

Par contre, si vous cliquez sur le lien sur la gauche dans la vue **Utilisation de la mémoire**, la vue du tas est organisée par nombre d’objets ; les objets d’un type particulier dont le nombre a le plus augmenté sont affichés en haut (en fonction de la colonne **Différence de nombre**).

## <a name="examine-performance-events"></a>Examiner les événements de performance

La vue **Événements** dans les Outils de diagnostic vous présente les différents événements qui se produisent pendant le débogage, tels que la définition d’un point d’arrêt ou une exécution pas à pas du code. Vous pouvez consulter des informations telles que la durée de l’événement (mesurée à partir de la dernière suspension du débogueur ou du démarrage de l’application). Par exemple, si vous parcourez le code pas à pas (F10, F11), la vue **Événements** vous indique la durée d’exécution de l’application entre l’étape précédente et l’étape actuelle.

![Vue Événements dans les Outils de diagnostic](../profiling/media/prof-tour-events.png "Outils de diagnostic - Afficher les événements")

 > [!NOTE]
 > Si vous avez Visual Studio Enterprise, vous pouvez également voir [Événements IntelliTrace](../debugger/intellitrace.md) sous cet onglet.

Les mêmes événements s’affichent aussi dans l’éditeur de code, sous la forme de conseils sur les performances.

![Conseils sur les performances dans la visite guidée du profilage](../profiling/media/prof-tour-perf-tips.png "Conseils sur les performances dans la visite guidée du profilage")

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>Examiner les événements d’accessibilité et de performance de l’interface utilisateur (UWP)

Dans vos applications UWP, vous pouvez activer **Analyse de l’IU** dans la fenêtre Outils de diagnostic. L’outil recherche les problèmes de performances ou d’accessibilité et les affiche dans la vue **Événements** pendant le débogage. Les descriptions des événements fournissent des informations qui peuvent aider à résoudre les problèmes.

![Afficher les événements d’analyse de l’IU dans les Outils de diagnostic](../profiling/media/prof-tour-ui-analysis.png "Outils de diagnostic - Afficher les événements d’analyse de l’IU")

## <a name="profile-release-builds-without-the-debugger"></a>Profiler les versions Release sans le débogueur

Vous pouvez utiliser les outils de profilage, tels que l’utilisation de l’UC et l’utilisation de la mémoire, avec le débogueur (voir les sections précédentes), ou vous pouvez les exécuter à l’aide du profileur de performances, qui vise à fournir une analyse des versions **Release**. Dans le profileur de performances, vous pouvez collecter des informations de diagnostic pendant l’exécution de l’application, puis examiner ces informations après l’arrêt de l’application. Pour plus d’informations sur les différentes approches, consultez [Exécution des outils de profilage avec ou sans le débogueur](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

![Profileur de performances](../profiling/media/prof-tour-performance-profiler.png "Profileur de performances")

Ouvrez le profileur de performances en choisissant **Déboguer/Profileur de performances**.

La fenêtre vous permet de sélectionner plusieurs outils de profilage dans certains scénarios. Les outils comme Utilisation de l’UC peuvent fournir des données complémentaires que vous pouvez utiliser dans votre analyse.

## <a name="analyze-resource-consumption-xaml"></a>Analyser la consommation des ressources (XAML)

Dans les applications XAML, telles que les applications WPF de bureau Windows et les applications du Windows Store, vous pouvez analyser la consommation des ressources à l’aide de l’outil Chronologie de l’application. Par exemple, vous pouvez analyser le temps passé par votre application à préparer les trames de l’interface utilisateur (mise en page et rendu), à traiter les demandes du réseau et des disques, et dans les scénarios comme le démarrage de l’application, le chargement des pages et le redimensionnement des fenêtres. Pour utiliser l’outil, choisissez **Chronologie de l’application** dans le profileur de performances, puis choisissez **Démarrer**. Dans votre application, effectuez le scénario susceptible de présenter un problème de consommation de ressources, puis choisissez **Arrêter la collecte** pour générer le rapport.

La présence de taux de trames faibles dans le graphique **Débit visuel** peut correspondre à des problèmes visuels que vous constatez quand vous exécutez votre application. De même, la présence de nombres élevés dans le graphique **Utilisation du thread d’interface utilisateur** peut également indiquer des problèmes de réactivité de l’interface utilisateur. Dans le rapport, vous pouvez sélectionner une période de temps susceptible de présenter un problème de performances, puis examiner les activités de thread de l’interface utilisateur détaillées dans la vue Détails de la chronologie (volet inférieur).

![Outil de profilage - Chronologie de l’application](../profiling/media/prof-tour-application-timeline.gif "Chronologie de l’application dans la visite guidée du profilage")

La vue Détails de la chronologie comprend des informations telles que le type d’activité (ou l’élément d’interface utilisateur impliqué), ainsi que la durée de l’activité. Par exemple, dans l’illustration, un événement **Layout** (disposition) pour un contrôle de grille prend 57,53 ms.

Pour plus d’informations, consultez [Chronologie de l’application](../profiling/application-timeline.md).

## <a name="analyze-gpu-usage-direct3d"></a>Analyser l’utilisation du GPU (Direct3D)

Dans les applications Direct3D (les composants Direct3D doivent être en C++), vous pouvez examiner l’activité sur le GPU et analyser les problèmes de performances. Pour plus d’informations, consultez [Utilisation du GPU](../debugger/gpu-usage.md). Pour utiliser l’outil, choisissez **Utilisation du GPU** dans le profileur de performances, puis choisissez **Démarrer**. Dans votre application, effectuez le scénario à profiler, puis choisissez **Arrêter la collecte** pour générer un rapport.

Quand vous sélectionnez une période de temps dans les graphiques et que vous choisissez **Afficher les détails**, une vue détaillée s’affiche dans le volet inférieur. Dans la vue détaillée, vous pouvez consulter le volume d’activité qui se produit sur chaque UC et GPU. Sélectionnez les événements dans le volet inférieur pour afficher des fenêtres contextuelles dans la chronologie. Par exemple, sélectionnez l’événement **Présent** pour afficher les fenêtres contextuelles des appels **Présent**. (Vous pouvez utiliser les lignes Vsync verticales gris clair pour déterminer si certains appels **Présent** ont manqué le Vsync. Il doit y avoir un appel **Présent** entre chaque paire de Vsyncs pour que l’application atteigne régulièrement 60 i/s.)

![Outil de profilage - Utilisation du GPU](../profiling/media/prof-tour-gpu-usage.png "Boîte de dialogue Utilisation du GPU")

Vous pouvez également utiliser les graphiques pour déterminer la présence éventuelle de goulots d’étranglement liés à l’UC ou au GPU.

## <a name="analyze-performance-javascript"></a>Analyser les performances (JavaScript)

Pour les applications HTML universelles Windows, vous pouvez utiliser les outils Mémoire JavaScript et Réactivité de l’interface utilisateur HTML.

L’outil Mémoire JavaScript est similaire à l’outil Utilisation de la mémoire disponible pour les autres types d’application. Vous pouvez utiliser cet outil pour comprendre l’utilisation de la mémoire et rechercher les fuites de mémoire dans votre application. Pour plus d’informations sur l’outil, consultez [Mémoire JavaScript](../profiling/javascript-memory.md).

![Outil de profilage - Mémoire JavaScript](../profiling/media/diagjsmemory.png "DiagJSMemory")

Pour diagnostiquer la réactivité de l’interface utilisateur, la lenteur du temps de chargement et la lenteur des mises à jour visuelles dans les applications HTML universelles Windows, utilisez l’outil Réactivité de l’interface utilisateur HTML. L’utilisation est similaire à l’outil Chronologie de l’application pour les autres types d’application. Pour plus d’informations, consultez [Réactivité de l’interface utilisateur HTML](../profiling/html-ui-responsiveness.md).

![Outil de profilage - Réactivité de l’interface utilisateur HTML](../profiling/media/diaghtmlresp.png "DiagHTMLResp")

## <a name="analyze-network-usage-uwp"></a>Analyser l’utilisation du réseau (UWP)

Dans les applications UWP, vous pouvez analyser les opérations réseau exécutées par le biais de l’API `Windows.Web.Http`. Cet outil peut vous aider à résoudre des problèmes tels que les problèmes d’accès et d’authentification, l’utilisation incorrecte du cache et les mauvaises performances d’affichage et de téléchargement. Pour utiliser l’outil, choisissez **Réseau** dans le profileur de performances, puis choisissez **Démarrer**. Dans votre application, effectuez le scénario qui utilise `Windows.Web.Http`, puis choisissez **Arrêter la collecte** pour générer le rapport.

![Outil de profilage - Utilisation du réseau](../profiling/media/prof-tour-network-usage.png "Boîte de dialogue Utilisation du réseau")

Sélectionnez une opération dans la vue du résumé pour afficher des informations plus détaillées.

![Informations détaillées dans l’outil Utilisation du réseau](../profiling/media/prof-tour-network-usage-details.png "Boîte de dialogue Détails de l’utilisation du réseau")

Pour plus d’informations, consultez [Utilisation du réseau](../profiling/network-usage.md).

## <a name="analyze-performance-legacy-tools"></a>Analyser les performances (outils hérités)

Si vous avez besoin de fonctionnalités qui ne sont pas présentes dans les outils Utilisation de l’UC ou Utilisation de la mémoire, telles que l’instrumentation, et que vous exécutez des applications de bureau ou ASP.NET, vous pouvez utiliser l’Explorateur de performances pour le profilage. (Non pris en charge dans les applications UWP). Pour plus d’informations, consultez [Explorateur de performances](../profiling/performance-explorer.md).

![Outil Explorateur de performances](../profiling/media/prof-tour-performance-explorer.png "Explorateur de performances")

## <a name="which-tool-should-i-use"></a>Quel outil utiliser ?  
Voici un tableau qui recense les différents outils proposés par Visual Studio, ainsi que les différents types de projet avec lesquels vous pouvez les utiliser :
  
|Outil d’analyse des performances|Bureau Windows|Universel Windows/Store|ASP.NET/ASP.NET Core|  
|----------------------|---------------------|------------------------------|-------------|  
|[Utilisation de la mémoire](../profiling/memory-usage.md)|oui|oui|oui|  
|[Utilisation de l’UC](../profiling/cpu-usage.md)|oui|oui|oui|  
|[Utilisation du GPU](../debugger/gpu-usage.md)|oui|oui|non|  
|[Chronologie de l’application](../profiling/application-timeline.md)|oui|oui|non|  
|[PerfTips](../profiling/perftips.md)|oui|oui pour XAML, non pour HTML|oui|  
|[Explorateur de performances](../profiling/performance-explorer.md)|oui|non|oui (non pour ASP.NET Core)|  
|[IntelliTrace](../debugger/intellitrace.md)|.NET Enterprise uniquement|.NET Enterprise uniquement|.NET Enterprise uniquement|
|[Utilisation du réseau](../profiling/network-usage.md)|non|oui|non| 
|[Réactivité de l’interface utilisateur HTML](../profiling/html-ui-responsiveness.md)|non|oui pour HTML, non pour XAML|non|  
|[Mémoire JavaScript](../profiling/javascript-memory.md)|non|oui pour HTML, non pour XAML|non|  

## <a name="see-also"></a>Voir aussi  
 [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)
