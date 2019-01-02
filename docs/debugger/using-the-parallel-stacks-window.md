---
title: Afficher les threads dans la fenêtre Piles parallèles | Microsoft Docs
ms.custom: ''
ms.date: 11/20/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4ee9d52f63f3158979f2f018ea44d5b68d6612c1
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2018
ms.locfileid: "53562332"
---
# <a name="view-threads-and-tasks-in-the-parallel-stacks-window"></a>Afficher les threads et les tâches dans la fenêtre Piles parallèles

Le **piles parallèles** fenêtre est utile pour déboguer des applications multithread. Il a plusieurs vues :

- [Vue threads](#threads-view) affiche les informations sur la pile d’appels pour tous les threads dans l’application. Vous pouvez naviguer entre les threads et les frames de pile sur ces threads. 

- [Mode tâches](#tasks-view) affiche des informations de pile d’appel centré sur la tâche. 
  - Dans le code managé, **tâches** vue affiche les piles d’appels de <xref:System.Threading.Tasks.Task?displayProperty=fullName> objets. 
  - En code natif, **tâches** vue affiche les piles d’appels de [groupes de tâches](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [algorithmes parallèles](/cpp/parallel/concrt/parallel-algorithms), [agents asynchrones](/cpp/parallel/concrt/asynchronous-agents)et [tâches légères](/cpp/parallel/concrt/task-scheduler-concurrency-runtime).  
  
- [Dans la vue méthode](#method-view) pivote de la pile des appels sur une méthode sélectionnée. 

## <a name="use-the-parallel-stacks-window"></a>Utiliser la fenêtre Piles parallèles 

Pour ouvrir le **piles parallèles** fenêtre, vous devez être dans une session de débogage. Sélectionnez **déboguer** > **Windows** > **piles parallèles**. 

### <a name="toolbar-controls"></a>Contrôles de barre d’outils

Le **piles parallèles** fenêtre possède les contrôles de barre d’outils suivants : 

![Barre d’outils dans la fenêtre Piles parallèles](../debugger/media/parallel_stackstoolbar.png "barre d’outils Piles parallèles")  
  
|Icône|Contrôle|Description|  
|-|-|-|  
|![Zone de liste déroulante threads/tâches](media/parallel_toolbar1.png "zone de liste déroulante Threads/tâches")|**Threads**/**tâches** zone de liste déroulante|Bascule entre la vue des piles d’appels de threads et la vue des piles d’appels de tâches. Pour plus d’informations, consultez [Vue Tâches](#tasks-view) et [Vue Threads](#threads-view).|  
|![Afficher l’icône uniquement avec indicateur](media/parallel_toolbar2.png "icône Afficher uniquement avec indicateur")|Afficher uniquement avec indicateur|Affiche les piles d’appels uniquement pour les threads qui sont marqués dans d’autres fenêtres du débogueur, telles que la **Threads GPU** fenêtre et la **espion parallèle** fenêtre.|  
|![Icône de la vue méthode bascule](media/parallel_toolbar3.png "icône de basculer dans la vue méthode")|Basculer dans la **vue Méthode**|Bascule entre les vues de pile des appels et **vue méthode**. Pour plus d’informations, consultez [Vue Méthode](#method-view).|  
|![Défilement automatique vers l’icône actuelle](media/parallel_toolbar4.png "défilement automatique vers l’icône actuelle")|Défilement automatique vers le frame de pile actif|Fait défiler automatiquement le graphique afin que le frame de pile actuel est dans la vue. Cette fonctionnalité est utile lorsque vous modifiez le frame de pile actuel d’autres fenêtres, ou lorsque vous atteignez un nouveau point d’arrêt dans les graphiques de grande taille.|  
|![Icône de Zoom bascule](media/parallel_toolbar5.png "icône Activer/désactiver Zoom")|Basculer le contrôle de zoom|Affiche ou masque le contrôle de zoom à gauche de la fenêtre. <br /><br />Quelle que soit la visibilité du contrôle de zoom, vous pouvez également effectuer un zoom avant en appuyant sur **Ctrl** et activation de la roulette de souris, ou en appuyant sur **Ctrl**+**MAJ** + **+** zoomer et **Ctrl**+**MAJ** + **-** effectuer un zoom arrière. |  
  
### <a name="stack-frame-icons"></a>Icônes de Frame de pile
Les icônes suivantes fournissent des informations sur les frames de pile actifs et actuels dans toutes les vues :

|Icône|Description|  
|-|-|  
|![Flèche jaune](media/icon_parallelyellowarrow.gif)|Indique l’emplacement actuel (frame de pile actif) du thread actuel.|
|![Icône de threads](media/icon_parallelthreads.gif)|Indique l’emplacement actuel (frame de pile actif) d’un thread non actuel.|
|![Flèche verte](media/icon_parallelgreenarrow.gif)|Indique le frame de pile actuel (le contexte actuel du débogueur). Le nom de la méthode est en gras, là où il apparaît.|  

### <a name="context-menu-items"></a>Éléments de menu contextuel  
Les éléments de menu de raccourci suivantes sont disponibles lorsque vous cliquez sur une méthode dans **Threads** vue ou **tâches** vue. Les six derniers éléments sont les mêmes que dans le [fenêtre Pile des appels](how-to-use-the-call-stack-window.md).  

![Menu contextuel dans la fenêtre Piles parallèles](../debugger/media/parallel_contmenu.png "menu contextuel dans la fenêtre Piles parallèles")  

|Menu Item|Description|  
|-|-|  
|**Marquer**|Marque l'élément sélectionné.|  
|**Supprimer l’indicateur**|Supprimer l'indicateur de l'élément sélectionné.|  
|**Figer**|Fige l'élément sélectionné.|  
|**Libérer**|Libère l'élément sélectionné.|  
|**Basculer vers le frame**|Même que le menu correspondant de commande dans le **pile des appels** fenêtre. Toutefois, dans le **piles parallèles** fenêtre, une méthode peut être dans plusieurs frames. Vous pouvez sélectionner l’image dans le sous-menu de cet élément. Si un des frames de pile se trouve sur le thread actuel, ce frame est sélectionné par défaut dans le sous-menu.|  
|**Accédez à la tâche** ou **atteindre le Thread**|Bascule vers le **tâche** ou **Threads** vue et conserve la même mise en surbrillance de frame de pile.|  
|**Atteindre le code source**|Accède à l’emplacement correspondant dans la fenêtre de code source. |  
|**Atteindre le code machine**|Accède à l’emplacement correspondant dans le **désassemblage** fenêtre.|  
|**Afficher le code externe**|Affiche ou masque le code externe.|  
|**Affichage hexadécimal**|Bascule entre affichage décimal et hexadécimal.|  
|**Afficher les threads dans la source**|Indicateurs de l’emplacement du thread dans la fenêtre de code source. |  
|**Informations sur le chargement de symboles**|Ouvre le **les informations de chargement de symboles** boîte de dialogue.|  
|**Paramètres des symboles**|Ouvre le **paramètres des symboles** boîte de dialogue. |  
  
## <a name="threads-view"></a>vue Threads  

Dans **Threads** afficher, le frame de pile et le chemin d’appel du thread actuel sont mis en surbrillance en bleu. L’emplacement actuel du thread est indiqué par la flèche jaune. 

Pour modifier le frame de pile en cours, double-cliquez sur une autre méthode. Cela peut également basculer le thread actuel, selon que la méthode sélectionnée fait partie du thread actuel ou un autre thread. 

Lorsque le **Threads** affiche un graphique est trop grand pour tenir dans la fenêtre, un **vue aérienne** contrôle apparaît dans la fenêtre. Vous pouvez déplacer le frame dans le contrôle pour accéder à différentes parties du graphique.  
  
L’illustration suivante montre un thread qui va du principal à un géré pour effectuer la transition du code natif. Six threads se trouvent dans la méthode actuelle. Un continue à Thread.Sleep et un autre continue à Console.WriteLine, puis à SyncTextWriter.WriteLine.  

 ![Vue dans la fenêtre Piles parallèles threads](../debugger/media/parallel_stack1.png "Threads vue dans la fenêtre Piles parallèles")  

Le tableau suivant décrit les principales fonctionnalités de la **Threads** vue :  
  
|Légende|Nom de l'élément|Description|  
|-|-|-|  
|1|Nœud ou segment de pile des appels|Contient une série de méthodes pour un ou plusieurs threads. Si le frame n’est flèche ligne connectés à celui-ci, l’image montre le chemin d’appel entier du ou des threads.|  
|2|Surbrillance bleue|Indique le chemin d’appel du thread actuel.|  
|3|Flèches|Relient des nœuds pour créer le chemin d’appel entier du ou des threads.|  
|4|En-tête de nœud|Affiche le nombre de processus et les threads pour le nœud.|  
|5|Méthode|Représente un ou plusieurs frames de pile dans la même méthode.|  
|6|Info-bulle sur (méthode)|S’affiche lorsque vous pointez sur une méthode. Dans **Threads** vue, l’info-bulle affiche tous les threads, dans un tableau similaire à la **Threads** fenêtre. |  

## <a name="tasks-view"></a>Vue Tâches  
Si votre application utilise <xref:System.Threading.Tasks.Task?displayProperty=fullName> objets (code managé) ou `task_handle` objets (code natif) pour exprimer le parallélisme, vous pouvez utiliser **tâches** vue. La vue **Tâches** contient les piles d’appels des tâches au lieu de celles des threads. 

Dans **tâches** vue :  
  
- Piles d’appels des threads qui ne sont pas en cours d’exécution des tâches ne sont pas visibles.  
- Piles d’appels des threads qui exécutent des tâches sont tronquées visuellement en haut et bas pour afficher les frames les plus pertinents pour les tâches.  
- Lorsque plusieurs tâches figurent sur un thread, les piles d’appels de ces tâches sont affichés dans des nœuds distincts.  

Pour afficher une pile d’appel entière, revenez à **Threads** affichage en effectuant un clic droit dans un frame de pile et en sélectionnant **atteindre le Thread**.  

L’illustration suivante montre le **Threads** affichage en haut et le correspondantes **tâches** vue en bas.  

![Vues de threads et les tâches](../debugger/media/parallel_threads-tasks.png "vues Threads et tâches")  

Pointez sur une méthode pour afficher une info-bulle avec des informations supplémentaires. Dans **tâches** , l’info-bulle affiche toutes les tâches dans une table semblable à la **tâches** fenêtre. 

L’illustration suivante montre l’info-bulle pour une méthode dans le **Threads** affichage en haut et correspondants **tâches** vue en bas.  

![Info-bulles des threads et tâches](../debugger/media/parallel_threads-tasks-tooltips.png "info-bulles des Threads et tâches")  

## <a name="method-view"></a>Vue Méthode  
À partir de le **Threads** vue ou **tâches** vue, vous pouvez faire pivoter le graphique sur la méthode actuelle en sélectionnant le **basculer dans la vue méthode** icône sur la barre d’outils. La **vue Méthode** présente toutes les méthodes de tous les threads qui appellent ou sont appelés par la méthode actuelle. L’illustration suivante montre la manière dont les mêmes informations apparaissent dans **Threads** afficher sur la gauche et dans **vue méthode** sur la droite.  

![Threads de vue et la vue méthode](../debugger/media/parallel_methodview.png "Threads vue et la vue méthode")  
  
Si vous basculez vers un nouveau frame de pile, vous faites de cette méthode la méthode actuelle, et **vue méthode** affiche tous les appelants et appelés pour la nouvelle méthode. Des threads peuvent alors apparaître ou disparaître de la vue, selon que cette méthode s'affiche ou non sur leurs piles des appels. Pour revenir à la vue de pile des appels, sélectionnez le **vue méthode** icône de barre d’outils à nouveau.  
  
## <a name="see-also"></a>Voir aussi  
 [Commencer à déboguer une application multithread](../debugger/get-started-debugging-multithreaded-apps.md)   
 [Procédure pas à pas : Déboguer une application parallèle](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Tout d’abord examiner le débogueur](../debugger/debugger-feature-tour.md) [débogage du code managé](../debugger/debugging-managed-code.md)   
 [Programmation parallèle](/dotnet/standard/parallel-programming/index)   
 [Utiliser la fenêtre Tâches](../debugger/using-the-tasks-window.md)   
 [Classe Task](../extensibility/debugger/task-class-internal-members.md)
