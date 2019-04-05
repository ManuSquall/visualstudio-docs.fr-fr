---
title: À l’aide de la parallèle de la fenêtre piles | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelstacks
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: f50efb78-5206-4803-bb42-426ef8133f2f
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df364440f544df663eff294dfd53dcd671dea049
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953049"
---
# <a name="using-the-parallel-stacks-window"></a>Utilisation de la fenêtre Piles parallèles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le **piles parallèles** fenêtre est utile lorsque vous déboguez des applications multithread. Son **vue Threads** affiche les informations sur la pile d’appels pour tous les threads dans votre application. Elle vous permet de naviguer entre les threads et les frames de pile sur ces threads. Dans le code managé, le **vue tâches** affiche les piles d’appels <xref:System.Threading.Tasks.Task?displayProperty=fullName> objets. En code natif, le **vue tâches** affiche les piles d’appels [groupes de tâches](http://msdn.microsoft.com/library/42f05ac3-2098-494a-ba84-737fcdcad077), [algorithmes parallèles](http://msdn.microsoft.com/library/045dca7b-4d73-4558-a44c-383b88a28473), [agents asynchrones](http://msdn.microsoft.com/library/6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a)et [tâches légères](http://msdn.microsoft.com/library/9aba278c-e0c9-4ede-b7c6-fedf7a365d90).  
  
## <a name="threads-view"></a>vue Threads  
 L'illustration suivante présente un thread qui est allé de Main vers A puis B et ensuite vers du code externe. Deux autres threads sont partis de code externe et sont allés vers A, mais l'un des deux a continué vers B, puis vers du code externe, tandis que l'autre a continué vers C, puis vers une AnonymousMethod.  
  
 ![Vue dans la fenêtre Piles parallèles threads](../debugger/media/parallel-stacksthread.png "Parallel_StacksThread")  
  
 Dans l’illustration, le chemin d’appel du thread actuel est mis en surbrillance en bleu et le frame de pile actif est signalé par la flèche jaune. Vous pouvez modifier le frame de pile actuel en sélectionnant une autre méthode dans le **piles parallèles** fenêtre. Ceci peut également entraîner le basculement du thread actuel, selon que la méthode sélectionnée fait déjà partie du thread actuel ou d'un autre thread. Le tableau suivant décrit les principales fonctionnalités de la **piles parallèles** fenêtre comme indiqué dans l’illustration.  
  
|Lettre de référence|Nom de l'élément|Description|  
|--------------------|------------------|-----------------|  
|A|Nœud ou segment de pile des appels|Contient une série de contextes de méthode pour un ou plusieurs threads. Si le nœud n'est pas relié à des flèches, il représente le chemin d'appel entier du ou des threads.|  
|B|Surbrillance bleue|Indique le chemin d’appel du thread actuel.|  
|C|Flèches|Relient des nœuds pour créer le chemin d'appel entier du ou des threads.|  
|D|Info-bulle sur l'en-tête de nœud|Indique l’ID et le nom défini par l’utilisateur de chaque thread dont le chemin d’appel partage ce nœud.|  
|E|Contexte de méthode|Représente un ou plusieurs frames de pile dans la même méthode.|  
|F|Info-bulle sur le contexte de méthode|Dans la vue Threads, il affiche tous les threads dans une table semblable à la **Threads** fenêtre. Dans la vue de la tâche, il affiche toutes les tâches dans une table semblable à la **tâches parallèles** fenêtre.|  
  
 En outre, la fenêtre Piles parallèles affiche une **vue aérienne** icône dans le volet principal lorsque le graphique est trop grand pour tenir dans la fenêtre. Vous pouvez cliquer sur l'icône pour afficher le graphique entier dans la fenêtre.  
  
## <a name="method-context-icons"></a>Icônes du contexte de méthode  
 Le tableau suivant décrit les icônes qui fournissent des informations sur les frames de pile actifs et actuels :  
  
|||  
|-|-|  
|Icône|Description|  
|![Flèche jaune des piles parallèles](../debugger/media/icon-parallelyellowarrow.gif "Icon_ParallelYellowArrow")|Indique que le contexte de méthode contient le frame de pile actif du thread actuel.|  
|![Icône Threads des piles parallèles](../debugger/media/icon-parallelthreads.gif "Icon_ParallelThreads")|Indique que le contexte de méthode contient le frame de pile actif d'un thread non actuel.|  
|![Flèche verte des piles parallèles](../debugger/media/icon-parallelgreenarrow.gif "Icon_ParallelGreenArrow")|Indique que le contexte de méthode contient le frame de pile actuel. Ce nom de méthode apparaît en gras dans tous les nœuds dans lesquels il s'affiche.|  
  
## <a name="toolbar-controls"></a>Contrôles de barre d'outils  
 L'illustration et le tableau suivants décrivent les contrôles disponibles dans la barre d'outils Piles parallèles.  
  
 ![Barre d’outils dans la fenêtre Piles parallèles](../debugger/media/parallel-stackstoolbar.png "Parallel_StacksToolbar")  
  
|Lettre de référence|Contrôle|Description|  
|--------------------|-------------|-----------------|  
|A|Zone de liste déroulante Threads/Tâches|Bascule entre la vue des piles d’appels de threads et la vue des piles d’appels de tâches. Pour plus d’informations, consultez Vue Tâches et Vue Threads.|  
|B|Afficher uniquement avec indicateur|Affiche les piles d’appels uniquement pour les threads qui sont marqués dans d’autres fenêtres de débogage, telles que la **Threads GPU** fenêtre et la **espion parallèle** fenêtre.|  
|C|Basculer dans la vue Méthode|Bascule entre la vue Pile et la vue Méthode. Pour plus d'informations, consultez Vue Méthode.|  
|D|Défilement automatique vers le frame de pile actif|Fait défiler automatiquement le diagramme afin que le frame de pile actuel soit visible. Cette fonctionnalité est utile lorsque vous modifiez le frame de pile actuel d’autres fenêtres ou lorsque vous atteignez un nouveau point d’arrêt dans de grands diagrammes.|  
|E|Basculer le contrôle de zoom|Affiche ou masque le contrôle de zoom. Vous pouvez également effectuer un zoom avant en appuyant sur CTRL et en activant la roulette de souris, indépendamment de la visibilité du contrôle de zoom, ou à l’aide de **CTRL + MAJ + '+'** zoomer et **CTRL + MAJ +'-'** effectuer un zoom arrière. En appuyant sur **CTRL + F8** applique un zoom avant pour s’ajuster à l’écran.|  
  
### <a name="context-menu-items"></a>Éléments de menu contextuel  
 L’illustration et le tableau suivants décrivent les éléments de menu contextuel disponibles lorsque vous cliquez avec le bouton droit sur un contexte de méthode dans la vue Threads ou la vue Tâches. Les six derniers éléments sont empruntés directement à la fenêtre Pile des appels et ne présentent aucun nouveau comportement.  
  
 ![Menu contextuel dans la fenêtre Piles parallèles](../debugger/media/parallel-contmenu.png "Parallel_ContMenu")  
  
|Élément de menu|Description|  
|---------------|-----------------|  
|Indicateur|Marque l'élément sélectionné.|  
|Supprimer l'indicateur|Supprimer l'indicateur de l'élément sélectionné.|  
|Figer|Fige l'élément sélectionné.|  
|Libérer|Libère l'élément sélectionné.|  
|Atteindre la tâche (thread)|Exécute la même fonction que la zone de liste déroulante de la barre d'outils, mais conserve le même frame de pile en surbrillance.|  
|Atteindre le code source|Accède à l'emplacement du code source qui correspond au frame de pile sur lequel l'utilisateur a cliqué avec le bouton droit.|  
|Basculer vers le frame|Identique à la commande de menu correspondante de la fenêtre Pile des appels. Toutefois, avec les piles parallèles, plusieurs frames peuvent correspondre à un seul contexte de méthode. Par conséquent, l'élément de menu comporte des sous-menus, qui représentent chacun un frame de pile spécifique. Si l'un des frames de pile se trouve sur le thread actuel, le menu qui correspond à ce frame de pile est sélectionné.|  
|Atteindre le code machine|Accède à l'emplacement de la fenêtre Code Machine qui correspond au frame de pile sur lequel l'utilisateur a cliqué avec le bouton droit.|  
|Afficher le code externe|Affiche ou masque le code externe.|  
|Affichage hexadécimal|Bascule entre affichage décimal et hexadécimal.|  
|Informations sur le chargement de symboles|Affiche la boîte de dialogue correspondante.|  
|Paramètres des symboles|Affiche la boîte de dialogue correspondante.|  
  
## <a name="tasks-view"></a>Vue Tâches  
 Si votre application utilise <xref:System.Threading.Tasks.Task?displayProperty=fullName> objets (code managé) ou `task_handle` objets (code natif) pour exprimer le parallélisme, vous pouvez utiliser la zone de liste déroulante dans la barre d’outils de la fenêtre Piles parallèles pour basculer vers *vue tâches*. La vue Tâches contient les piles d'appels des tâches et non celles des threads. Les différences entre la vue Tâches et la vue Threads sont les suivantes :  
  
- Les piles d’appels des threads qui n’exécutent pas de tâches n’apparaissent pas.  
  
- Les piles d'appels des threads qui exécutent des tâches sont tronquées visuellement en haut et en bas afin d'afficher les frames les plus pertinents appartenant aux tâches.  
  
- Lorsque plusieurs tâches figurent sur un thread, les piles d'appels de ces tâches sont fractionnées dans des nœuds séparés.  
  
  L’illustration suivante présente la vue Tâches de la fenêtre Piles parallèles à droite et la vue Threads correspondante à gauche.  
  
  ![Tâches d’affichage dans la fenêtre Piles parallèles](../debugger/media/parallel-tasksview.png "Parallel_TasksView")  
  
  Pour afficher la pile des appels complète, passez simplement en vue Threads en double-cliquant sur un frame de pile, puis sur **atteindre le Thread**.  
  
  Comme indiqué dans le tableau précédent, vous pouvez afficher des informations supplémentaires en pointant le curseur de la souris sur un contexte de méthode. L'image suivante présente les informations de l'info-bulle pour la vue Threads et la vue Tâches.  
  
  ![Info-bulles dans la fenêtre Piles parallèles](../debugger/media/parallel-stack-tooltips.png "Parallel_Stack_Tooltips")  
  
## <a name="method-view"></a>Vue Méthode  
 À partir de la vue Threads ou de la vue Tâches, vous pouvez faire pivoter le graphique sur la méthode actuelle en cliquant sur l'icône Vue Méthode de la barre d'outils. La vue Méthode présente toutes les méthodes de tous les threads qui appellent ou sont appelés par la méthode actuelle. L'illustration suivante présente une vue Threads, ainsi que la façon dont les mêmes informations s'affichent dans la vue Méthode.  
  
 ![Dans la fenêtre Piles parallèles dans la vue méthode](../debugger/media/parallel-methodview.png "Parallel_MethodView")  
  
 En passant à un nouveau frame de pile, vous faites de cette méthode la méthode actuelle et affichez dans la fenêtre tous les appelants et appelés de cette méthode. Des threads peuvent alors apparaître ou disparaître de la vue, selon que cette méthode s'affiche ou non sur leurs piles des appels. Pour repasser en vue Pile, cliquez à nouveau sur le bouton de barre d'outils Vue Méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Débogage d’une Application parallèle](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Principes de base du débogueur](../debugger/debugger-basics.md)   
 [Débogage du code managé](../debugger/debugging-managed-code.md)   
 [Programmation parallèle](http://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [À l’aide de la fenêtre tâches](../debugger/using-the-tasks-window.md)   
 [Procédure pas à pas : Débogage d’une Application parallèle](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Classe Task](../extensibility/debugger/task-class-internal-members.md)
