---
title: Afficher les threads dans la fenêtre piles parallèles | Microsoft Docs
description: Utilisez des piles parallèles pour déboguer les applications multithread. Vous pouvez afficher les informations de pile pour tous les threads et les informations de pile des appels centrés sur les tâches.
ms.custom: SEO-VS-2020
ms.date: 11/20/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelstacks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: f50efb78-5206-4803-bb42-426ef8133f2f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7b92f4e2faf2043c26c7119b6f9754edd3bdc990
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884388"
---
# <a name="view-threads-and-tasks-in-the-parallel-stacks-window-c-visual-basic-c"></a>Afficher les threads et les tâches dans la fenêtre piles parallèles (C#, Visual Basic, C++)

La fenêtre **Piles parallèles** est utile pour déboguer des applications multithread. Il comporte plusieurs vues :

- La [vue threads](#threads-view) affiche les informations de la pile des appels pour tous les threads de l’application. Vous pouvez naviguer entre les threads et les frames de pile sur ces threads.

- La [vue tâches](#tasks-view) affiche les informations de la pile des appels centrés sur les tâches.
  - En code managé, la vue **tâches** affiche les piles d’appels des <xref:System.Threading.Tasks.Task?displayProperty=fullName> objets.
  - En code natif, la vue **tâches** affiche les piles d’appels des [groupes de tâches](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), des [algorithmes parallèles](/cpp/parallel/concrt/parallel-algorithms), des [agents asynchrones](/cpp/parallel/concrt/asynchronous-agents)et des [tâches légères](/cpp/parallel/concrt/task-scheduler-concurrency-runtime).

- La [vue méthode](#method-view) pivote la pile des appels sur une méthode sélectionnée.

## <a name="use-the-parallel-stacks-window"></a>Utiliser la fenêtre Piles parallèles

Pour ouvrir la fenêtre **Piles parallèles** , vous devez être dans une session de débogage. Sélectionnez **Déboguer** les  >    >  **Piles parallèles** Windows.

### <a name="toolbar-controls"></a>Contrôles de barre d’outils

La fenêtre **Piles parallèles** contient les contrôles de barre d’outils suivants :

![Barre d'outils dans la fenêtre Piles parallèles](../debugger/media/parallel_stackstoolbar.png "Barre d’outils piles parallèles")

|Icône|Control|Description|
|-|-|-|
|![Zone de liste déroulante Threads/Tâches](media/parallel_toolbar1.png "Zone de liste déroulante Threads/Tâches")|**Threads** / Zone de liste déroulante **tâches**|Bascule entre la vue des piles d’appels de threads et la vue des piles d’appels de tâches. Pour plus d’informations, consultez [Vue Tâches](#tasks-view) et [Vue Threads](#threads-view).|
|![Icône Afficher uniquement les indicateurs](media/parallel_toolbar2.png "Icône Afficher uniquement les indicateurs")|Afficher uniquement avec indicateur|Affiche les piles d’appels uniquement pour les threads signalés dans d’autres fenêtres du débogueur, telles que la fenêtre **Threads GPU** et la fenêtre **Espion parallèle** .|
|![Icône activer/désactiver la vue de méthode](media/parallel_toolbar3.png "Icône activer/désactiver la vue de méthode")|Basculer dans la **vue Méthode**|Bascule entre les vues de la pile des appels et la **vue méthode**. Pour plus d’informations, consultez [Vue Méthode](#method-view).|
|![Défilement automatique jusqu’à l’icône actuelle](media/parallel_toolbar4.png "Défilement automatique jusqu’à l’icône actuelle")|Défilement automatique vers le frame de pile actif|Fait défiler le graphique de manière automatique pour que le frame de pile en cours soit affiché. Cette fonctionnalité est utile lorsque vous modifiez le frame de pile actuel d’autres fenêtres ou lorsque vous atteignez un nouveau point d’arrêt dans de grands graphiques.|
|![Icône activer/désactiver le zoom](media/parallel_toolbar5.png "Icône activer/désactiver le zoom")|Basculer le contrôle de zoom|Affiche ou masque le contrôle de zoom à gauche de la fenêtre. <br /><br />Quelle que soit la visibilité du contrôle de zoom, vous pouvez également effectuer un zoom en appuyant sur **CTRL** et en faisant tourner la roulette de la souris, ou en appuyant sur **CTRL** + **MAJ** + **+** pour effectuer un zoom avant et sur **CTRL** + **MAJ** + **-** pour effectuer un zoom arrière. |

### <a name="stack-frame-icons"></a>Icônes de frame de pile
Les icônes suivantes fournissent des informations sur les frames de pile actifs et actuels dans toutes les vues :

|Icône|Description|
|-|-|
|![Flèche jaune](media/icon_parallelyellowarrow.gif)|Indique l’emplacement actuel (frame de pile actif) du thread actuel.|
|![Icône de threads](media/icon_parallelthreads.gif)|Indique l’emplacement actuel (frame de pile actif) d’un thread non actuel.|
|![Flèche verte](media/icon_parallelgreenarrow.gif)|Indique le frame de pile actuel (contexte du débogueur actuel). Le nom de la méthode est en gras partout où il apparaît.|

### <a name="context-menu-items"></a>Éléments de menu contextuel
Les éléments de menu contextuel suivants sont disponibles lorsque vous cliquez avec le bouton droit sur une méthode dans la vue **Threads** ou la vue **tâches** . Les six derniers éléments sont les mêmes que dans la [fenêtre pile des appels](how-to-use-the-call-stack-window.md).

![Menu Raccourci dans la fenêtre Piles parallèles](../debugger/media/parallel_contmenu.png "Menu Raccourci dans la fenêtre Piles parallèles")

|Élément de menu|Description|
|-|-|
|**Indicateur**|Marque l'élément sélectionné.|
|**Supprimer l’indicateur**|Supprimer l'indicateur de l'élément sélectionné.|
|**Freeze**|Fige l'élément sélectionné.|
|**Congelé**|Libère l'élément sélectionné.|
|**Basculer vers le frame**|Identique à la commande de menu correspondante dans la fenêtre **pile des appels** . Toutefois, dans la fenêtre **Piles parallèles** , une méthode peut être dans plusieurs frames. Vous pouvez sélectionner le frame de votre choix dans le sous-menu de cet élément. Si l’un des frames de pile se trouve sur le thread actuel, ce frame est sélectionné par défaut dans le sous-menu.|
|**Atteindre la tâche** ou **atteindre le thread**|Bascule vers la vue **tâche** ou **Threads** , et conserve le même frame de pile mis en surbrillance.|
|**Atteindre le code source**|Accède à l’emplacement correspondant dans la fenêtre de code source. |
|**Atteindre le code machine**|Accède à l’emplacement correspondant dans la fenêtre **code machine** .|
|**Afficher le code externe**|Affiche ou masque le code externe.|
|**Affichage hexadécimal**|Bascule entre affichage décimal et hexadécimal.|
|**Afficher les threads dans la source**|Marque l’emplacement du thread dans la fenêtre de code source. |
|**Informations sur le chargement de symboles**|Ouvre la boîte de dialogue **informations sur le chargement de symboles** .|
|**Paramètres des symboles**|Ouvre la boîte de dialogue **paramètres des symboles** . |

## <a name="threads-view"></a>vue Threads

Dans la vue **Threads** , le frame de pile et le chemin d’appel du thread actuel sont mis en surbrillance en bleu. L’emplacement actuel du thread est représenté par la flèche jaune.

Pour modifier le frame de pile en cours, double-cliquez sur une autre méthode. Cela peut également changer le thread actuel, selon que la méthode que vous sélectionnez fait partie du thread actuel ou d’un autre thread.

Lorsque le graphique de la vue **Threads** est trop grand pour tenir dans la fenêtre, le contrôle **d’affichage œil d’un oiseau** s’affiche dans la fenêtre. Vous pouvez déplacer le frame dans le contrôle pour accéder aux différentes parties du graphique.

L’illustration suivante montre un thread qui passe de main à une transition de code managé en code natif. Six threads se trouvent dans la méthode actuelle. L’un continue à thread. Sleep et un autre continue à console. WriteLine, puis à SyncTextWriter. WriteLine.

 ![Vue Threads dans la fenêtre Piles parallèles](../debugger/media/parallel_stack1.png "Vue Threads dans la fenêtre Piles parallèles")

Le tableau suivant décrit les principales fonctionnalités de la vue **Threads** :

|Légende|Nom de l'élément|Description|
|-|-|-|
|1|Nœud ou segment de pile des appels|Contient une série de méthodes pour un ou plusieurs threads. Si aucune ligne de flèche n’est connectée au frame, le frame affiche le chemin d’accès complet du ou des threads.|
|2|Surbrillance bleue|Indique le chemin d’appel du thread actuel.|
|3|Flèches|Relient des nœuds pour créer le chemin d'appel entier du ou des threads.|
|4|En-tête de nœud|Affiche le nombre de processus et de threads pour le nœud.|
|5|Méthode|Représente un ou plusieurs frames de pile dans la même méthode.|
|6|ToolTip sur la méthode|S’affiche lorsque vous pointez sur une méthode. Dans la vue **Threads** , l’info-bulle affiche tous les threads, dans une table similaire à la fenêtre **Threads** . |

## <a name="tasks-view"></a>Vue Tâches
Si votre application utilise des <xref:System.Threading.Tasks.Task?displayProperty=fullName> objets (code managé) ou des `task_handle` objets (code natif) pour exprimer le parallélisme, vous pouvez utiliser la vue **tâches** . La vue **Tâches** contient les piles d’appels des tâches au lieu de celles des threads.

Dans la vue **tâches** :

- Les piles d’appels des threads qui n’exécutent pas de tâches ne sont pas affichées.
- Les piles d’appels des threads qui exécutent des tâches sont tronquées visuellement en haut et en bas, afin d’afficher les frames les plus pertinents pour les tâches.
- Lorsque plusieurs tâches sont sur un thread, les piles d’appels de ces tâches sont affichées dans des nœuds distincts.

Pour afficher l’intégralité de la pile des appels, revenez à la vue **Threads** en cliquant avec le bouton droit sur un frame de pile et en sélectionnant **atteindre le thread**.

L’illustration suivante montre la vue **Threads** en haut et la vue **tâches** correspondante en bas.

![Vues threads et tâches](../debugger/media/parallel_threads-tasks.png "Vues threads et tâches")

Pointez sur une méthode pour afficher une info-bulle avec des informations supplémentaires. Dans la vue **tâches** , l’info-bulle affiche toutes les tâches d’un tableau semblable à la fenêtre **tâches** .

L’illustration suivante montre l’info-bulle d’une méthode dans la vue **Threads** en haut et pour la vue **tâches** correspondante en bas.

![Info-bulles de threads et de tâches](../debugger/media/parallel_threads-tasks-tooltips.png "Info-bulles de threads et de tâches")

## <a name="method-view"></a>Vue Méthode
À partir de la vue **Threads** ou de la vue **tâches** , vous pouvez faire pivoter le graphique sur la méthode actuelle en sélectionnant l’icône **basculer la vue méthode** dans la barre d’outils. La **vue Méthode** présente toutes les méthodes de tous les threads qui appellent ou sont appelés par la méthode actuelle. L’illustration suivante montre comment les mêmes informations s’affichent dans la vue **Threads** à gauche et dans la **vue méthode** à droite.

![Vue threads et vue méthode](../debugger/media/parallel_methodview.png "Vue threads et vue méthode")

Si vous basculez vers un nouveau frame de pile, vous faites de cette méthode la méthode actuelle, et la **vue méthode** affiche tous les appelants et les appelants de la nouvelle méthode. Des threads peuvent alors apparaître ou disparaître de la vue, selon que cette méthode s'affiche ou non sur leurs piles des appels. Pour revenir à l’affichage de la pile des appels, cliquez à nouveau sur l’icône de la barre d’outils de la **vue méthode** .

## <a name="see-also"></a>Voir aussi
- [Prise en main du débogage d’une application multithread](../debugger/get-started-debugging-multithreaded-apps.md)
- [Procédure pas à pas : Déboguer une application parallèle](../debugger/walkthrough-debugging-a-parallel-application.md)
- [Présentation du débogueur](../debugger/debugger-feature-tour.md)
- [Débogage de code managé](../debugger/debugging-managed-code.md)
- [Programmation parallèle](/dotnet/standard/parallel-programming/index)
- [Utiliser la fenêtre Tâches](../debugger/using-the-tasks-window.md)
- [Classe de tâche](../extensibility/debugger/task-class-internal-members.md)
