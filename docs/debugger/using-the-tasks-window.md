---
title: "À l’aide de la fenêtre tâches | Documents Microsoft"
ms.custom: 
ms.date: 04/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.paralleltasks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0b1d4f79be83f69989064ed7699df43b6930040
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2017
---
# <a name="using-the-tasks-window"></a>Utilisation de la fenêtre Tâches
Le **tâches** fenêtre ressemble à la **Threads** fenêtre, à ceci près qu’elle affiche des informations sur <xref:System.Threading.Tasks.Task?displayProperty=fullName>, [task_handle](/cpp/parallel/concrt/reference/task-group-class.md), ou [WinJS.Promise ](http://msdn.microsoft.com/library/windows/apps/br211867.aspx) des objets au lieu de chaque thread. Comme les threads, les tâches représentent des opérations asynchrones qui peuvent s’exécuter simultanément. Toutefois, plusieurs tâches peuvent s’exécuter sur le même thread. 
  
 Dans le code managé, vous pouvez utiliser la **tâches** fenêtre lorsque vous travaillez avec <xref:System.Threading.Tasks.Task?displayProperty=fullName> objets ou avec le **await** et **async** mots clés (**Await** et **Async** en Visual Basic). Pour plus d’informations sur les tâches en code managé, consultez [programmation parallèle](/dotnet/standard/parallel-programming/index).  
  
 En code natif, vous pouvez utiliser la **tâches** fenêtre lorsque vous travaillez avec [groupes de tâches](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [algorithmes parallèles](/cpp/parallel/concrt/parallel-algorithms), [agents asynchrones](/cpp/parallel/concrt/asynchronous-agents), et [tâches légères](/cpp/parallel/concrt/task-scheduler-concurrency-runtime). Pour plus d’informations sur les tâches en code natif, consultez [Runtime d’accès concurrentiel](/cpp/parallel/concrt/concurrency-runtime).  
  
 Dans JavaScript, vous pouvez utiliser la fenêtre tâches lorsque vous travaillez avec promesse `.then` code. Consultez [programmation asynchrone dans JavaScript (applications UWP)](http://msdn.microsoft.com/library/windows/apps/hh700330.aspx) pour plus d’informations.   
  
 Vous pouvez utiliser la **tâches** fenêtre chaque fois que vous arrêtez dans le débogueur. Vous pouvez y accéder sur le **déboguer** en cliquant sur **Windows** , puis en cliquant sur **tâches**. L’illustration suivante montre le **tâches** fenêtre dans son mode par défaut.  
  
 ![La fenêtre tâches](../debugger/media/parallel_tasks_window.png "Parallel_Tasks_Window")  
  
> [!NOTE]
>  En code managé, <xref:System.Threading.Tasks.Task> qui a un état <xref:System.Threading.Tasks.TaskStatus>, <xref:System.Threading.Tasks.TaskStatus> ou <xref:System.Threading.Tasks.TaskStatus>, ne peut pas s'afficher dans la fenêtre Tâches lorsque les threads managés sont à l'état de veille ou à l'état de jonction.  
  
## <a name="tasks-column-information"></a>Informations sur les colonnes de la fenêtre Tâches  
 Les colonnes dans le **tâches** fenêtre Afficher les informations suivantes.  
  
|Nom de la colonne|Description|  
|-----------------|-----------------|  
|**Indicateurs**|Affiche les tâches avec indicateur et vous permet d’ajouter un indicateur à une tâche ou d’en supprimer un.|  
|**Icônes**|La flèche jaune indique la tâche actuelle. La tâche actuelle est la tâche supérieure du thread actuel.<br /><br /> Une flèche blanche indique la tâche d'arrêt, autrement dit, celle qui était actuelle lorsque le débogueur a été appelé.<br /><br /> L'icône de pause indique une tâche gelée par l'utilisateur. Vous pouvez geler et libérer une tâche en cliquant dessus avec le bouton droit dans la liste.|  
|**ID**|Numéro fourni par le système pour la tâche. En code natif, il s’agit de l’adresse de la tâche.|  
|**État**|État actuel (planifié, actif, bloqué, en attente ou terminé) de la tâche. Une tâche planifiée est une tâche qui n'a pas encore été exécutée et, par conséquent, qui de possède pas encore une pile d'appels, un thread assigné ou des informations connexes.<br /><br /> Une tâche active est une tâche qui était en train d'exécuter du code avant de s'arrêter dans le débogueur.<br /><br /> Une tâche en attente est une tâche bloquée qui attend le signal d'un événement, la libération d'un verrouillage ou la fin d'une autre tâche.<br /><br /> Une tâche bloquée est une tâche en attente dont le thread est bloqué par un autre thread.<br /><br /> Placez le curseur sur le **état** cellule d’une tâche bloquée ou en attente pour plus d’informations sur le blocage. **Avertissement :** le **tâches** fenêtre signale les interblocages uniquement pour les tâches bloquées utilisant une primitive de synchronisation prise en charge par Wait Chain Traversal (WCT). Par exemple, pour un interblocage <xref:System.Threading.Tasks.Task> objet, qui utilise le WCT, le débogueur signale **attente bloquée**. Pour une tâche bloquée gérée par le Runtime d’accès concurrentiel, qui n’utilise pas Wait Chain Traversal, le débogueur signale **attente**. Pour plus d’informations sur WCT, consultez [Wait Chain Traversal](http://msdn.microsoft.com/library/ms681622\(VS.85\).aspx).|  
|**Heure de début**|Heure à laquelle la tâche est devenue active.|  
|**Durée**|Nombre de secondes durant lesquelles la tâche a été active.|  
|**Heure de fin**|Heure à laquelle la tâche s’est terminée.|  
|**Emplacement**|Emplacement actuel dans la pile d’appels de la tâche. Pointez sur cette cellule pour visualiser l'ensemble de la pile des appels de la tâche. Les tâches planifiées ne disposent pas de valeur dans cette colonne.|  
|**Task**|Méthode initiale et tous les arguments passés à la tâche lorsqu’elle a été créée.|  
|**Parent**|ID de la tâche qui a créé cette tâche. Si rien n'est indiqué, la tâche n'a aucun parent. Ceci s'applique uniquement aux programmes gérés.|  
|**Affectation de thread**|ID et nom du thread sur lequel la tâche s’exécute.|  
|**État de retour**|État de la tâche lorsqu’elle est terminée. Les valeurs de retour d’état sont **réussite**, **annulé**, et **erreur**.|  
|**Domaine d’application**|Pour du code managé, domaine d’application dans lequel la tâche s’exécute.|  
|**task_group**|Pour le code natif, l’adresse de la [task_group](/cpp/parallel/concrt/reference/task-group-class.mdd) objet qui a planifié la tâche. Pour les agents asynchrones et les tâches légères, cette colonne a la valeur 0.|  
|Processus|ID du processus que la tâche exécute.|  
|État asynchrone|En matière de code managé, état de la tâche. Par défaut, cette colonne est masquée. Pour afficher cette colonne, ouvrez le menu contextuel pour l'une des en-têtes de colonnes. Choisissez **colonnes**, **AsyncState**.|  
  
 Vous pouvez ajouter des colonnes à la vue en cliquant avec le bouton droit sur un en-tête de colonne et en sélectionnant ensuite les colonnes souhaitées. (Supprimez des colonnes en effaçant les sélections.) Vous pouvez également réorganiser les colonnes en les faisant glisser à gauche ou à droite. Le menu contextuel des colonnes est présenté dans l'illustration suivante.  
  
 ![Menu Affichage de raccourci dans la fenêtre tâches](../debugger/media/parallel_tasks_contextmenu.png "Parallel_Tasks_ContextMenu")  
  
## <a name="sorting-tasks"></a>Tri de tâches  
 Pour trier des tâches en fonction des critères de colonne, cliquez sur l’en-tête d’une colonne. Par exemple, en cliquant sur le **ID** en-tête de colonne, vous pouvez trier les tâches par ID de tâche : 1,2,3,4,5 et ainsi de suite. Pour inverser l'ordre de tri, cliquez à nouveau sur l'en-tête de la colonne. La colonne et l'ordre de tri actuels sont indiqués par une flèche dans la colonne.  
  
## <a name="grouping-tasks"></a>Regroupement de tâches  
 Vous pouvez regrouper des tâches en fonction d’une colonne de la vue Liste. Par exemple, en double-cliquant sur le **état** en-tête de colonne, puis cliquez sur **Grouper par état**, vous pouvez regrouper toutes les tâches qui ont le même état. Par exemple, vous pouvez visualiser rapidement les tâches en attente afin de vous concentrer sur la raison de leur blocage. Vous pouvez également réduire un groupe qui ne présente pas d'intérêt pour la session de débogage. De la même manière, vous pouvez regrouper les tâches en fonction des autres colonnes. Pour ajouter un indicateur à un groupe (ou en supprimer un), il suffit de cliquer sur le bouton en regard de l'en-tête de groupe. L’illustration suivante montre le **tâches** fenêtre en mode regroupé.  
  
 ![Mode groupé dans la fenêtre tâches](../debugger/media/parallel_tasks_groupedmode.png "Parallel_Tasks_GroupedMode")  
  
## <a name="parent-child-view"></a>Vue Parent enfant  
 (cette vue est uniquement disponible pour le code managé) En cliquant sur un en-tête de colonne, puis sur **Vue Parent enfant**, vous pouvez modifier la liste des tâches en une vue hiérarchique, dans les enfants de chaque tâche est un sous-nœud qui peut être affiché ou masqué sous son parent. L’illustration suivante présente les tâches au sein de la vue parent-enfant.  
  
 ![Parent &#45; enfant à afficher dans la fenêtre tâches](../debugger/media/parallel_tasks_parentchildview.png "Parallel_Tasks_ParentChildView")  
  
## <a name="flagging-tasks"></a>Ajout d’indicateurs à des tâches  
 Vous pouvez marquer le thread sur lequel une tâche s’exécute en sélectionnant la tâche, puis en choisissant **indicateur** dans le menu contextuel, ou en cliquant sur l’icône d’indicateur dans la première colonne. Si vous signalez plusieurs tâches, vous pouvez ensuite effectuer un tri sur la colonne d’indicateur pour déplacer toutes les tâches avec indicateur vers le haut afin de pouvoir vous concentrer uniquement sur celles-ci. Vous pouvez également utiliser le **piles parallèles** pour afficher uniquement les tâches avec indicateur. Cela vous permet d’éliminer par filtrage les tâches qui ne vous intéressent pas pour le débogage. Les indicateurs ne sont pas persistants entre les sessions de débogage.  
  
## <a name="freezing-and-thawing-tasks"></a>Gel et libération des tâches  
 Vous pouvez geler le thread sur lequel une tâche est en cours d’exécution en cliquant sur l’élément de liste de tâches, puis sur **verrouiller le Thread affecté**. (Si une tâche est déjà gelée, la commande est **libérer le Thread affecté**.) Lorsque vous gelez un thread, celui-ci ne s'exécute pas lorsque vous parcourez le code après le point d'arrêt actuel. Le **verrouiller tous les Threads sauf celui-ci** commande gèle tous les threads sauf celui qui exécute la tâche.  
  
 L’illustration suivante présente les autres éléments de menu pour chaque tâche.  
  
 ![Menu contextuel du thread dans la fenêtre tâches](../debugger/media/parallel_tasks_contextmenu2.png "Parallel_Tasks_ContextMenu2")  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base du débogueur](../debugger/debugger-basics.md)   
 [Débogage du code managé](../debugger/debugging-managed-code.md)   
 [Programmation parallèle](/dotnet/standard/parallel-programming/index)   
 [Runtime d’accès concurrentiel](/cpp/parallel/concrt/concurrency-runtime)   
 [À l’aide de la fenêtre Piles parallèles](../debugger/using-the-parallel-stacks-window.md)   
 [Procédure pas à pas : débogage d’une application parallèle](../debugger/walkthrough-debugging-a-parallel-application.md)