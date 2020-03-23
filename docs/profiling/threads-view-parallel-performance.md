---
title: Vue Threads dans le visualiseur concurrentiel | Microsoft Docs
ms.date: 11/04/2018
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threadblocking
helpviewer_keywords:
- Concurrency Visualizer, Threads View (Parallel Performance)
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4382a21a68848a758f3d4cd37a8528722927691c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62973750"
---
# <a name="threads-view-in-the-concurrency-visualizer"></a>Vue Threads dans le visualiseur concurrentiel

La vue **Threads** est la vue la plus détaillée et la plus riche en fonctionnalités du visualiseur concurrentiel. Dans la vue **Threads**, vous pouvez identifier les threads qui exécutent du code pendant un segment d’exécution et analyser si les threads s’exécutent ou se bloquent à cause d’une synchronisation, des E/S ou autres. La vue **Threads** signale également l’exécution de l’arborescence de la pile des appels des profils et les threads de déblocage.

Pendant que les threads s’exécutent, le visualiseur concurrentiel collecte des échantillons. Quand un thread arrête de s’exécuter, le visualiseur examine tous les événements de changement de contexte du système d’exploitation du thread. Des changements de contexte peuvent se produire pour les raisons suivantes :

- Un thread est bloqué sur une primitive de synchronisation.
- Le quantum d’un thread expire.
- Un thread effectue une demande d’E/S bloquante.

Le visualiseur concurrentiel classe les événements de changement de contexte et de thread, puis recherche des API reconnues bloquantes dans les piles des appels des threads. Il affiche les catégories de thread dans la légende active en bas à gauche de la vue **Threads**. Dans la plupart des cas, vous pouvez identifier la cause principale d’un événement de blocage en examinant les piles des appels qui correspondent aux événements de changement de contexte.

Si aucune pile d’appels ne correspond, le visualiseur concurrentiel utilise la raison d’attente fournie par [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]. Cependant, la catégorie de [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] peut être basée sur un détail de l’implémentation et ne pas refléter l’intention de l’utilisateur. Par exemple, [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] indique la raison de l’attente du blocage sur un verrou de lecteur-enregistreur natif comme étant une E/S alors qu’il s’agit d’une synchronisation.

La vue **Threads** affiche également les dépendances entre les threads. Par exemple, si vous identifiez un thread qui est bloqué sur un objet de synchronisation, vous pouvez trouver le thread qui l’a débloqué. Vous pouvez examiner la pile des appels du thread de déblocage au moment où il a débloqué l’autre thread.

Vous pouvez utiliser la vue **Threads** pour :

- Identifier les raisons pour lesquelles l’interface utilisateur d’une application ne répond pas pendant certaines phases de l’exécution.
- Déterminer la quantité de temps passée dans des blocages liés à la synchronisation, à des E/S, à des erreurs de page et à d’autres événements.
- Découvrir le niveau d’interférence provenant d’autres processus qui s’exécutent sur le système.
- Identifier les problèmes d’équilibrage de charge pour l’exécution parallèle.
- Rechercher les raisons d’une scalabilité non optimale ou inexistante. Par exemple, pourquoi les performances d’une application parallèle ne s’améliorent pas alors que d’autres cœurs logiques sont disponibles.
- Comprendre le degré de concurrence dans l’application, pour optimiser la parallélisation.
- Identifier les dépendances entre les threads worker et les chemins critiques de l’exécution.

## <a name="use-threads-view"></a>Utiliser la vue Threads

Pour démarrer Concurrency Visualizer, **sélectionnez Analyze** > **Concurrency Visualizer,** puis sélectionnez une option, comme **Le lancement d’un nouveau processus**.

Le visualiseur concurrentiel démarre l’application et collecte une trace jusqu’à ce que vous sélectionniez **Arrêter la collecte**. Le visualiseur analyse ensuite la trace et affiche les résultats dans la page de rapport de la trace.

Sélectionnez l’onglet **Threads** en haut à gauche du rapport pour ouvrir la vue **Threads**.

![Vue de fils](../profiling/media/threadsviewnarrowing.png "vue Threads")

Sélectionnez les intervalles de temps et les threads pour démarrer une analyse des performances.

## <a name="timeline-analysis"></a>Analyse de la chronologie

La partie supérieure de la vue **Threads** est une chronologie. La chronologie montre l’activité de tous les threads du processus et de toutes les unités de disque physique de l’ordinateur hôte. Il affiche également l’activité GPU et les événements de marqueur.

Dans la chronologie, l’axe des X représente le temps et l’axe Y représente plusieurs canaux :

- Deux canaux d’E/S pour chaque lecteur de disque sur le système, un canal pour les lectures et un pour les écritures.
- Un canal pour chaque thread du processus.
- Des canaux de marqueurs, s’il existe des événements de marqueur dans la trace. Les canaux de marqueurs apparaissent initialement sous les canaux de threads qui ont généré ces événements.
- Canaux GPU

Initialement, les threads sont triés dans l’ordre où ils sont créés : le thread d’application principal figure donc en premier. Sélectionnez une autre option dans le menu déroulant **Trier par** pour trier les threads par un autre critère comme **Exécution**.

Les couleurs de la chronologie indiquent l’état d’un thread à un moment donné. Les segments verts indiquent qu’il est en cours d’exécution, les rouges qu’il est bloqué pour la synchronisation, les jaunes qu’il est préempté et les violets qu’il est engagé dans les E/S d’un appareil.

Vous pouvez effectuer un zoom avant pour voir plus de détails, ou un zoom arrière pour voir un intervalle de temps plus long. Sélectionnez des segments et des points sur le graphe pour obtenir des détails sur les catégories, les heures de début, les retards et les états de la pile des appels.

Utilisez la chronologie pour examiner la répartition du travail entre les threads impliqués dans une boucle parallèle ou dans des tâches concurrentes. Si l’exécution d’un thread est plus longue que celle des autres, le travail est peut-être déséquilibré. Vous pouvez améliorer les performances de votre application en distribuant le travail de façon plus uniforme entre les threads.

Si un seul thread est en cours d’exécution à un point dans le temps, l’application risque de ne pas tirer pleinement parti de la concurrence sur le système. Vous pouvez utiliser le graphe chronologique pour examiner les dépendances entre les threads, et les relations chronologiques entre les threads de blocage et les threads bloqués. Pour réorganiser les threads, sélectionnez un thread et l’icône Monter ou Descendre dans la barre d’outils.

Vous pouvez masquer les threads qui ne font aucun travail ou qui sont complètement bloqués, car leurs statistiques ne sont pas pertinentes et peuvent polluer les rapports. Masquez les threads en sélectionnant leur nom, puis en sélectionnant les icônes **Masquer les threads sélectionnés** ou **Masquer tous les threads sauf ceux sélectionnés** dans la barre d’outils. Pour identifier les threads à masquer, sélectionnez le lien **Synthèse par thread** en bas à gauche. Vous pouvez masquer les threads qui ne présentent aucune activité dans le graphe **Synthèse par thread**.

### <a name="thread-execution-details"></a>Détails de l’exécution d’un thread
Pour obtenir des informations plus détaillées sur un segment d’exécution, sélectionnez un point sur un segment vert de la chronologie. Le visualiseur concurrentiel affiche un signe d’insertion noir au-dessus du point sélectionné et montre sa pile des appels sous l’onglet **Actuel** du volet inférieur. Vous pouvez sélectionner plusieurs points sur le segment d’exécution.

>[!NOTE]
>Le visualiseur concurrentiel risque de ne pas pouvoir résoudre une sélection sur un segment d’exécution si la durée du segment est inférieure à une milliseconde.

Pour obtenir un profil d’exécution pour tous les threads non masqués dans la période de temps sélectionnée, sélectionnez **Exécution** dans la légende en bas à gauche.

### <a name="thread-blocking-details"></a>Détails du blocage d’un thread
Pour obtenir des informations sur une région particulière sur un thread, placez le pointeur sur cette région dans la chronologie pour afficher une info-bulle. L’info-bulle contient des informations comme la catégorie, l’heure de début et le retard. Sélectionnez la région pour afficher la pile des appels à ce point précis dans le temps sous l’onglet **Actuel** du volet inférieur. Le volet affiche également la catégorie, le retard, ainsi que l’API de blocage et le thread de déblocage le cas échéant. En examinant la pile des appels, vous pouvez déterminer les raisons sous-jacentes des événements de blocage du thread.

Un chemin d’exécution peut avoir plusieurs événements de blocage. Pour les examiner par catégorie de blocage et trouver plus rapidement les zones à problème, sélectionnez une catégorie de blocage dans la légende à gauche.

### <a name="dependencies-between-threads"></a>Dépendances entre threads
Le visualiseur concurrentiel affiche les dépendances entre les threads, ce qui vous permet de déterminer ce qu’un thread bloqué tentait de faire et ce que d’autres threads lui ont permis d’exécuter.

Pour déterminer quel thread a débloqué un autre thread, sélectionnez le segment de blocage dans la chronologie. Si le visualiseur concurrentiel peut déterminer le thread de déblocage, il trace une ligne entre le thread de déblocage et le segment d’exécution qui suit le segment de blocage. Sélectionnez l’onglet **Pile de déblocage** dans le volet inférieur pour voir la pile des appels appropriée.

## <a name="profile-reports"></a>Rapports des profils
Sous le graphe de la chronologie se trouve un volet avec les onglets de rapport **Rapport des profils**, **Actuel** et **Pile de déblocage**. Les rapports se mettent à jour automatiquement quand vous changez la chronologie et les sélections de threads. Pour les grandes traces, le volet des rapports risque de ne pas être disponible pendant le calcul des mises à jour.

### <a name="profile-report-tab"></a>Onglet Rapport des profils

Le **Rapport des profils** présente deux filtres :

- Pour filtrer les entrées de l’arborescence des appels où peu de temps a été passé, tapez une valeur de filtre entre 0 et 99 pour cent dans le champ **Réduction du bruit à**. La valeur par défaut est 2 pour cent.
- Pour voir les arborescences des appels seulement pour votre code, cochez la case **Uniquement mon code**. Pour voir toutes les arborescences des appels, décochez-la.

L’onglet **Rapport des profils** montre les rapports des catégories et des liens de la légende. Pour afficher un rapport, sélectionnez une des entrées sur la gauche :

- **Exécution** Le rapport **Exécution** montre la répartition du temps d’exécution de l’application.

  Pour rechercher la ligne de code où le temps d’exécution est passé, développez l’arborescence des appels et, dans le menu contextuel pour l’entrée de l’arborescence des appels, sélectionnez **Afficher la source** ou **Afficher les sites d’appel**. **Afficher la source** localise la ligne de code exécutée. **Afficher les sites d’appel** localise la ligne de code qui a appelé la ligne exécutée. S’il n’existe qu’une seule ligne de site d’appel, son code est mis en surbrillance. Si plusieurs sites d’appels existent, sélectionnez celui de votre choix dans la boîte de dialogue, puis sélectionnez **Atteindre la source**. Il est souvent utile de localiser le site d’appel ayant le plus grand nombre d’instances, la durée la plus longue ou les deux. Pour plus d’informations, consultez [Rapport de profil d’exécution](../profiling/execution-profile-report.md).

- **Synchronisation** Le rapport **Synchronisation** montre les appels responsables des blocages de synchronisation ainsi que les durées totales de blocage pour chaque pile des appels. Pour plus d’informations, consultez [Durée de synchronisation](../profiling/synchronization-time.md).

- **E/S** Le rapport **E/S** montre les appels responsables des blocages d’E/S ainsi que les durées totales de blocage pour chaque pile des appels. Pour plus d’informations, consultez [Temps d’E/S (vue Threads)](../profiling/i-o-time-threads-view.md).

- **Veille** Le rapport **Veille** montre les appels responsables des blocages de veille ainsi que les durées totales de blocage pour chaque pile des appels. Pour plus d’informations, voir [Temps de sommeil](../profiling/sleep-time.md).

- **Gestion de la mémoire** Le rapport **Gestion de la mémoire** montre les appels où les blocages de gestion de la mémoire se sont produits ainsi que les durées totales de blocage pour chaque pile des appels. Utilisez ces informations pour identifier les zones qui ont des problèmes de pagination ou de garbage collection excessifs.  Pour plus d’informations, voir [le temps de gestion de la mémoire](../profiling/memory-management-time.md).

- **Anticipation** Le rapport **Anticipation** montre où les processus sur le système ont anticipé le processus en cours. Il montre également les threads individuels qui ont remplacé les threads du processus en cours. Vous pouvez utiliser ces informations pour identifier les processus et les threads qui ont effectué le plus de préemptions. Pour plus d’informations, voir [Temps de Préemption](../profiling/preemption-time.md).

- **Traitement de l’interface utilisateur** Le rapport **Traitement de l’interface utilisateur** montre les appels responsables des blocages de traitement de l’IU ainsi que les durées totales de blocage pour chaque pile des appels. Pour plus d’informations, voir [le temps de traitement de l’interface utilisateur](../profiling/ui-processing-time.md).

- **Synthèse par thread** Sélectionnez **Synthèse par thread** pour afficher un graphe indiquant l’état des threads pendant l’intervalle de temps sélectionné. Les colonnes avec des codes de couleur montrent la durée totale que chaque thread a passée dans les états En cours d’exécution, Bloqué, E/S et autres. Les threads sont nommés en bas. Quand vous ajustez le niveau de zoom dans le graphe chronologique, celui-ci se met automatiquement à jour.

  À certains niveaux de zoom, certains threads risquent de ne pas apparaître dans le graphe. Si cela se produit, des points de suspension (**...**) s’affichent à droite. Si le thread que vous voulez n’apparaît pas, vous pouvez masquer d’autres threads. Pour plus d’informations, consultez [Rapport Récapitulatif par thread](../profiling/per-thread-summary-report.md).

- **Opérations sur le disque** Sélectionnez **Opérations sur le disque** pour afficher les processus et les threads impliqués dans les E/S disque du processus en cours, les fichiers qu’ils ont utilisés (par exemple les DLL qu’ils ont chargées), le nombre d’octets lus et d’autres informations. Vous pouvez utiliser ce rapport pour évaluer le temps passé à accéder aux fichiers pendant l’exécution, en particulier quand votre processus est lié à des E/S. Pour plus d’informations, consultez [Rapport Opérations sur le disque](../profiling/disk-operations-report-threads-view.md).

### <a name="current-tab"></a>Onglet actuel
Cet onglet affiche la pile des appels pour un point sélectionné sur un segment de thread dans le graphique chronologique. Les piles des appels sont coupées de façon à afficher seulement les activités liées à votre application.

### <a name="unblocking-stack-tab"></a>Onglet Pile de déblocage
Cet onglet affiche le thread qui a débloqué le thread sélectionné et la pile des appels de déblocage.

## <a name="see-also"></a>Voir aussi
- [Visualiseur concurrentiel](../profiling/concurrency-visualizer.md)
