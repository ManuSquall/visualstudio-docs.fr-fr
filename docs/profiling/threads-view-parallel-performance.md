---
title: Vue Threads (Performances parallèles) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threadblocking
helpviewer_keywords:
- Concurrency Visualizer, Threads View (Parallel Performance)
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 80ce83bba65affcb47a702d572d8d962f712667e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49883989"
---
# <a name="threads-view-parallel-performance"></a>Threads, vue (niveau de performance parallèle)
**L’Affichage Threads** est le mode le plus détaillé et le plus riche en fonctionnalités du visualiseur concurrentiel (choisissez **Analyser** > **Visualiseur concurrentiel** pour démarrer le visualiseur concurrentiel). En utilisant cette vue, vous pouvez déterminer si les threads sont en cours d’exécution ou s’ils sont bloqués à cause d’une synchronisation, d’E/S ou pour une autre raison.  
  
 Pendant l’analyse du profil, le visualiseur concurrentiel examine tous les événements de changement de contexte du système d’exploitation pour chaque thread de l’application. Les changements de contexte peuvent se produire pour de nombreuses raisons, comme celles-ci :  
  
- Un thread est bloqué sur une primitive de synchronisation.  
  
- Le quantum d’un thread expire.  
  
- Un thread effectue une demande d’E/S bloquante.  
  
  La vue Threads affecte une catégorie à chaque changement de contexte quand un thread a cessé de s’exécuter. Les catégories sont indiquées dans la légende qui figure dans la partie inférieure gauche de la vue. Le visualiseur concurrentiel catégorise les événements de changement de contexte en recherchant dans la pile des appels du thread les API notoirement bloquantes. S’il n’existe pas de correspondance dans la pile des appels, la raison de l’attente fournie par [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] est utilisée. Cependant, la catégorie de [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] peut être basée sur un détail de l’implémentation et ne pas refléter l’intention de l’utilisateur. Par exemple, [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] indique la raison de l’attente du blocage sur un verrou de lecteur-enregistreur natif comme étant une E/S alors qu’il s’agit d’une synchronisation. Dans la plupart des cas, vous pouvez identifier la cause principale d’un événement de blocage en examinant les piles des appels qui correspondent aux événements de changement de contexte.  
  
  La vue Threads affiche également les dépendances entre les threads. Par exemple, si vous identifiez un thread qui est bloqué sur un objet de synchronisation, vous pouvez rechercher le thread qui l’a débloqué et vous pouvez examiner l’activité sur la pile des appels pour ce thread au moment où il a débloqué l’autre.  
  
  Quand des threads sont en cours d’exécution, le visualiseur concurrentiel collecte des échantillons. Dans la vue Threads, vous pouvez déterminer quel code est exécuté par un ou plusieurs threads pendant un segment d’exécution. Vous pouvez également examiner des rapports de blocage et des rapports qui profilent l’exécution de l’arborescence de la pile des appels.  
  
## <a name="usage"></a>Utilisation  
 Voici quelques façons d’utiliser la vue Threads :  
  
-   Identifier les raisons pour lesquelles l’interface utilisateur d’une application ne répond pas pendant certaines phases de l’exécution.  
  
-   Déterminer la quantité de temps passée dans des blocages liés à la synchronisation, à des E/S, à des défauts de page et à d’autres événements.  
  
-   Identifier le niveau d’interférence provenant d’autres processus qui s’exécutent sur le système.  
  
-   Identifier les problèmes d’équilibrage de charge pour l’exécution parallèle.  
  
-   Identifier les raisons pour lesquelles la scalabilité est sous-optimisée ou inexistante (par exemple pourquoi les performances d’une application parallèle ne s’améliorent pas quand plus de cœurs logiques sont disponibles).  
  
-   Comprendre le degré de concurrence dans l’application, pour optimiser la parallélisation.  
  
-   Comprendre les dépendances entre les threads Worker et les chemins critiques de l’exécution.  
  
## <a name="examine-specific-time-intervals-and-threads"></a>Examiner les intervalles de temps et les threads spécifiques  
 La vue Threads montre une chronologie. Vous pouvez effectuer un zoom et un panoramique dans la chronologie pour examiner des intervalles spécifiques et des threads de votre application. Le temps figure sur l’axe des X et plusieurs canaux sont présents sur l’axe Y :  
  
- Deux canaux d’E/S pour chaque lecteur de disque sur le système, un canal pour les lectures et un pour les écritures.  
  
- Un canal pour chaque thread du processus.  
  
- Des canaux de marqueurs, s’il existe des événements de marqueur dans la trace. Les canaux de marqueurs apparaissent initialement sous les canaux de threads qui ont généré ces événements.  
  
- Canaux GPU  
  
  Voici une illustration de la vue Threads :  
  
  ![Vue threads](../profiling/media/threadsviewnarrowing.png "ThreadsViewNarrowing")  
  vue Threads  
  
  Initialement, les threads sont triés dans l’ordre où ils sont créés : le thread d’application principal figure donc en premier. Vous pouvez utiliser l’option de tri dans le coin supérieur gauche de la vue pour trier les threads selon un autre critère (par exemple sur la base de la plus grande quantité de travail d’exécution effectuée).  
  
  Vous pouvez masquer les threads qui n’effectuent pas de travail en sélectionnant leur nom dans la colonne de gauche, puis en choisissant **Masquer les threads sélectionnés** dans la barre d’outils. Nous vous recommandons de masquer les threads qui sont complètement bloqués, car leurs statistiques ne sont pas pertinentes et peuvent encombrer les rapports.  
  
  Pour identifier des threads supplémentaires à masquer, dans la légende active, sélectionnez le rapport **Résumé par thread** sous l’onglet **Rapport des profils**. Ceci affiche le graphique de répartition de l’exécution, qui montre l’état des threads pour l’intervalle de temps sélectionné. À certains niveaux de zoom, certains threads peuvent ne pas être affichés. Quand cela se produit, des points de suspension sont affichés à droite.  
  
  Quand vous avez sélectionné un intervalle de temps et certains threads qui y apparaissent, vous pouvez démarrer l’analyse des performances.  
  
## <a name="analysis-tools"></a>Outils d’analyse  
 Cette section décrit les rapports et d’autres outils d’analyse.  
  
### <a name="thread-blocking-details"></a>Détails du blocage d’un thread  
 Pour obtenir des informations sur un événement de blocage dans une région particulière sur un thread, placez le pointeur sur cette zone pour afficher une info-bulle. Elle contient des informations comme la catégorie, l’heure de début de la région, la durée du blocage et, le cas échéant, une API de blocage. Si vous sélectionnez la région de blocage, la pile à ce stade dans le temps s’affiche dans le volet inférieur, avec les mêmes informations que celles qui sont affichées dans l’info-bulle. En examinant la pile des appels, vous pouvez déterminer la raison sous-jacente de l’événement de blocage du thread. Vous pouvez trouver des informations supplémentaires sur les processus et les threads en sélectionnant le segment et en examinant l’onglet Actuel.  
  
 Un chemin d’exécution peut avoir plusieurs événements de blocage. Vous pouvez les examiner par catégorie de blocage, ce qui vous permet de trouver plus rapidement les zones de problèmes. Choisissez simplement une des catégories de blocages dans la légende à gauche.  
  
### <a name="dependencies-between-threads"></a>Dépendances entre threads  
 Le visualiseur concurrentiel peut afficher les dépendances entre les threads dans votre processus, ce qui vous permet de déterminer ce qu’un thread bloqué tentait de faire et de découvrir ce que d’autres threads lui ont permis d’exécuter. Pour déterminer quel thread a débloqué un autre thread, sélectionnez le segment de blocage approprié. Si le visualiseur concurrentiel peut déterminer le thread de déblocage, il trace une ligne entre le thread de déblocage et le segment d’exécution qui suit le segment de blocage. En outre, l’onglet **Pile de déblocage** montre la pile des appels appropriée.  
  
### <a name="thread-execution-details"></a>Détails de l’exécution d’un thread  
 Dans le graphique chronologique d’un thread, les segments verts indiquent les moments où il exécutait du code. Vous pouvez obtenir des informations plus détaillées sur un segment d’exécution.  
  
 Quand vous sélectionnez un point dans un segment d’exécution, le visualiseur concurrentiel recherche ce point dans le temps sur la pile des appels appropriée, puis affiche un signe d’insertion noir au-dessus du point sélectionné dans le segment d’exécution et affiche la pile des appels elle-même sous l’onglet **Pile active**. Vous pouvez sélectionner plusieurs points sur le segment d’exécution.  
  
> [!NOTE]
>  Le visualiseur concurrentiel n’est parfois pas en mesure de résoudre une sélection sur un segment d’exécution. En général, ceci se produit quand la durée du segment est inférieure à 1 milliseconde.  
  
 Pour obtenir un profil d’exécution pour tous les threads activés (non masqués) dans la période de temps sélectionnée, choisissez le bouton **Exécution** dans la légende active.  
  
### <a name="timeline-graph"></a>Graphe de chronologie  
 Le graphique chronologique montre l’activité de tous les threads dans le processus et de tous les appareils de disque physique sur l’ordinateur hôte. Il affiche également l’activité GPU et les événements de marqueur.  Vous pouvez effectuer un zoom avant pour afficher plus de détails ou un zoom arrière pour afficher un intervalle de temps plus long. Vous pouvez également sélectionner des points sur le graphique pour obtenir des détails sur les catégories, les heures de début, les durées et les états de la pile des appels.  
  
 Dans le graphique chronologique, une couleur indique l’état d’un thread à un moment donné. Par exemple, les segments verts ont été en cours d’exécution, les segments rouges ont été bloqués pour la synchronisation, les segments jaunes ont été préemptés et les segments violets ont été engagés dans les E/S d’un appareil. Vous pouvez utiliser cette vue pour la répartition de la charge de travail entre les threads impliqués dans une boucle parallèle ou dans des tâches concurrentes. Si l’exécution d’un thread est plus longue que celle des autres, le travail est peut-être déséquilibré. Vous pouvez utiliser ces informations pour améliorer les performances de votre programme en distribuant le travail de façon plus uniforme entre les threads.  
  
 Si un thread seulement est vert (en exécution) à un point dans le temps, l’application ne tire peut-être pas pleinement parti de la concurrence sur le système. Vous pouvez utiliser le graphique chronologique pour examiner les dépendances entre les threads et les relations chronologiques entre les threads de blocage et les threads bloqués. Pour réorganiser les threads, sélectionnez un thread puis, sur la barre d’outils, choisissez le bouton Monter ou Descendre. Pour masquer les threads, sélectionnez-les puis choisissez le bouton **Masquer les threads**.  
  
### <a name="profile-reports"></a>Rapports des profils  
 Sous le graphique chronologique, vous pouvez voir un profil chronologique et un volet avec des onglets pour les différents rapports. Les rapports se mettent à jour automatiquement quand vous modifiez la vue Threads. Dans le cas de traces de grande taille, il est possible que le volet des rapports soit indisponible pendant le calcul des mises à jour. Chaque rapport peut être ajusté via deux filtres : Réduction du bruit et Uniquement mon code. Réduction du bruit permet d’exclure les entrées de l’arborescence des appels ayant consommé peu de temps. La valeur par défaut du filtre est de 2 %, mais vous pouvez le régler de 0 à 99 %. Pour voir l’arborescence des appels seulement pour votre code, cochez la case **Uniquement mon code**. Pour voir toutes les arborescences des appels, décochez-la.  
  
#### <a name="profile-report"></a>Rapport des profils  
 Cet onglet affiche des rapports qui correspondent aux entrées figurant dans la légende active. Pour afficher un rapport, choisissez une des entrées.  
  
#### <a name="current-stack"></a>Pile active  
 Cet onglet affiche la pile des appels pour un point sélectionné sur un segment de thread dans le graphique chronologique. Les piles des appels sont élaguées de façon à afficher seulement les activités liées à votre programme.  
  
#### <a name="unblocking-stack"></a>Pile de déblocage  
 Pour voir quel thread a débloqué le thread sélectionné et à quelle ligne du code, choisissez l’onglet **Pile de déblocage**.  
  
#### <a name="execution"></a>Exécution  
 Le rapport Exécution montre la répartition du temps passé par l’application dans l’exécution.  
  
 Pour rechercher la ligne de code où le temps d’exécution est passé, développez l’arborescence des appels et, dans le menu contextuel pour l’entrée de l’arborescence des appels, choisissez **Afficher la source** ou **Afficher les sites d’appel**. **Afficher la source** localise la ligne de code exécutée. **Afficher les sites d’appel** localise la ligne de code qui a appelé la ligne de code exécutée. S’il n’existe qu’un seul site d’appel, la ligne de code est mise en surbrillance. S’il existe plusieurs sites d’appel, vous pouvez sélectionner celui de votre choix dans la boîte de dialogue qui s’affiche puis choisir le bouton **Atteindre la source** pour mettre en surbrillance le code du site d’appel. Il est souvent utile de localiser le site d’appel ayant le plus grand nombre d’instances, la durée la plus longue ou les deux. Pour plus d’informations, consultez [Rapport de profil d’exécution](../profiling/execution-profile-report.md).  
  
#### <a name="synchronization"></a>Synchronisation  
 Le rapport Synchronisation montre les appels responsables des blocages de synchronisation, ainsi que les durées totales de blocage pour chaque pile des appels. Pour plus d’informations, consultez [Durée de synchronisation](../profiling/synchronization-time.md).  
  
#### <a name="io"></a>E/S  
 Le rapport E/S montre les appels responsables des blocages d’E/S, ainsi que les durées totales de blocage pour chaque pile des appels. Pour plus d’informations, consultez [Temps d’E/S (vue Threads)](../profiling/i-o-time-threads-view.md).  
  
#### <a name="sleep"></a>Sleep  
 Le rapport de veille montre les appels responsables des blocages de veille, ainsi que les durées totales de blocage pour chaque pile des appels. Pour plus d’informations, consultez [Durée de veille](../profiling/sleep-time.md).  
  
#### <a name="memory-management"></a>Gestion de la mémoire  
 Le rapport de gestion de la mémoire montre les appels où les blocages de gestion de la mémoire se sont produits, ainsi que le total des temps de blocage pour chaque pile des appels. Vous pouvez utiliser ces informations pour identifier les zones qui ont des problèmes de pagination ou de garbage collection excessifs.  Pour plus d’informations, consultez [Période de gestion de la mémoire](../profiling/memory-management-time.md).  
  
#### <a name="preemption"></a>Anticipation  
 Le rapport Préemption montre les instances où les processus sur le système ont préempté le processus en cours et les threads individuels qui ont remplacé des threads dans le processus en cours. Vous pouvez utiliser ces informations pour identifier les processus et les threads qui ont effectué le plus de préemptions. Pour plus d’informations, consultez [Durée de préemption](../profiling/preemption-time.md).  
  
#### <a name="ui-processing"></a>Traitement de l'interface utilisateur  
 Le rapport de traitement de l’interface utilisateur montre les appels responsables des blocages de traitement de l’IU, ainsi que les durées totales de blocage pour chaque pile des appels. Pour plus d’informations, consultez [Temps de traitement UI](../profiling/ui-processing-time.md).  
  
#### <a name="per-thread-summary"></a>Récapitulatif par thread  
 Cet onglet affiche une vue en colonnes avec des codes de couleur de la durée totale que chaque thread a passé dans les états En cours d’exécution, Bloqué, E/S et dans d’autres états. Le libellé des colonnes se trouve dans le bas. Quand vous ajustez le niveau de zoom dans le graphique chronologique, cet onglet est automatiquement mis à jour. À certains niveaux de zoom, certains threads peuvent ne pas être affichés. Quand cela se produit, des points de suspension sont affichés à droite. Si le thread que vous voulez n’apparaît pas, vous pouvez masquer d’autres threads. Pour plus d’informations, consultez [Rapport Récapitulatif par thread](../profiling/per-thread-summary-report.md).  
  
#### <a name="disk-operations"></a>Opérations sur le disque  
 Cet onglet affiche les processus et les threads impliqués dans les E/S disque pour le compte du processus en cours, les fichiers qu’ils ont utilisés (par exemple les DLL qui ont été chargées), le nombre d’octets lus et d’autres informations. Vous pouvez utiliser ce rapport pour évaluer le temps passé dans les accès aux fichiers pendant l’exécution, en particulier quand votre processus est lié à des E/S. Pour plus d’informations, consultez [Rapport Opérations sur le disque](../profiling/disk-operations-report-threads-view.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Visualiseur concurrentiel](../profiling/concurrency-visualizer.md)