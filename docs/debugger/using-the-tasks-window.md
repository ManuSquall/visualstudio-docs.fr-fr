---
title: Utilisation de la fenêtre tâches | Microsoft Docs
ms.date: 03/18/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.paralleltasks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b32dc6372a6ce4983e9bd11e05a4a662d0ad44ba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62901583"
---
# <a name="using-the-tasks-window-c-visual-basic-c"></a>Utilisation de la fenêtre tâches (C#, Visual Basic, C++)

La fenêtre **Tâches** ressemble à la fenêtre **Threads**, hormis le fait qu'elle comporte des informations sur les objets <xref:System.Threading.Tasks.Task?displayProperty=fullName> , [task_handle](/cpp/parallel/concrt/reference/task-group-class) ou [WinJS.Promise](/previous-versions/windows/apps/br211867(v=win.10)), et non pas sur chaque thread. Comme les threads, les tâches représentent des opérations asynchrones qui peuvent s'exécuter simultanément. Toutefois, plusieurs tâches peuvent s'exécuter sur le même thread.

Le code managé vous permet d’utiliser la fenêtre **Tâches** lorsque vous travaillez avec des objets <xref:System.Threading.Tasks.Task?displayProperty=fullName> ou avec les mots clés **await** et **async** (**Await** et **Asynchrone** en Visual Basic). Pour plus d’informations sur les tâches en code managé, consultez  [programmation parallèle](/dotnet/standard/parallel-programming/index).

En code natif, vous pouvez utiliser la fenêtre **Tâches** lorsque vous travaillez avec des [groupes de tâches](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), des [algorithmes parallèles](/cpp/parallel/concrt/parallel-algorithms), des [agents asynchrones](/cpp/parallel/concrt/asynchronous-agents) et des [tâches légères](/cpp/parallel/concrt/task-scheduler-concurrency-runtime). Pour plus d’informations sur les tâches en code natif, consultez [Runtime d’accès concurrentiel](/cpp/parallel/concrt/concurrency-runtime).

En JavaScript, vous pouvez utiliser la fenêtre tâches lorsque vous utilisez le code de promesse `.then` . Pour plus d’informations, consultez [programmation asynchrone dans JavaScript (applications UWP)](/previous-versions/windows/apps/hh700330(v=win.10)) .

Vous pouvez utiliser la fenêtre **Tâches** chaque fois que l’exécution s’arrête dans le débogueur. Pour y accéder, dans le menu **Déboguer**, cliquez sur **Fenêtres**, puis sur **Tâches**. L’illustration suivante présente la fenêtre **Tâches** dans son mode par défaut.

![Fenêtre tâches](../debugger/media/parallel_tasks_window.png "Parallel_Tasks_Window")

> [!NOTE]
> Dans le code managé, un <xref:System.Threading.Tasks.Task> qui a l’état [TaskStatus. created](<xref:System.Threading.Tasks.TaskStatus.Created>), [TaskStatus. WaitingForActivation](<xref:System.Threading.Tasks.TaskStatus.WaitingForActivation>)ou [TaskStatus. WaitingToRun](<xref:System.Threading.Tasks.TaskStatus.WaitingToRun>) peut ne pas s’afficher dans la fenêtre **tâches** lorsque les threads managés sont dans un état de veille ou de jointure.

## <a name="tasks-column-information"></a>Informations sur les colonnes de la fenêtre Tâches

Les colonnes de la fenêtre **Tâches** contiennent les informations suivantes.

|Nom de la colonne|Description|
|-----------------|-----------------|
|**Indicateurs**|Affiche les tâches avec indicateur et vous permet d’ajouter un indicateur à une tâche ou d’en supprimer un.|
|**Icônes**|La flèche jaune indique la tâche actuelle. La tâche actuelle est la tâche supérieure du thread actuel.<br /><br /> Une flèche blanche indique la tâche d’arrêt, autrement dit, celle qui était actuelle lorsque le débogueur a été appelé.<br /><br /> L'icône de pause indique une tâche gelée par l'utilisateur. Vous pouvez geler et libérer une tâche en cliquant dessus avec le bouton droit dans la liste.|
|**Identifiant**|Numéro fourni par le système pour la tâche. En code natif, il s’agit de l’adresse de la tâche.|
|**Statut**|État actuel (planifié, actif, bloqué, bloqué, en attente ou terminé) de la tâche. Une tâche planifiée est une tâche qui n’a pas encore été exécutée et, par conséquent, qui de possède pas encore une pile d’appels, un thread assigné ou des informations connexes.<br /><br /> Une tâche active est une tâche qui était en train d'exécuter du code avant de s'arrêter dans le débogueur.<br /><br /> Une tâche en attente ou bloquée est une tâche qui est bloquée, car elle attend un événement à signaler, un verrou à libérer ou une autre tâche à terminer.<br /><br /> Une tâche bloquée est une tâche en attente dont le thread est bloqué par un autre thread.<br /><br /> Pointez sur la cellule **État** d’une tâche bloquée ou en attente pour obtenir plus d’informations sur le bloc. **Avertissement :**  La fenêtre **tâches** signale un blocage uniquement pour une tâche bloquée qui utilise une primitive de synchronisation prise en charge par le parcours de chaîne d’attente (WCT). Par exemple, pour un objet bloqué <xref:System.Threading.Tasks.Task> , qui utilise WCT, le débogueur signale **en attente**d’un blocage. Pour une tâche bloquée gérée par le runtime d’accès concurrentiel qui n’utilise pas Wait Chain Traversal, le débogueur signale **En attente**. Pour plus d'informations sur WCT, consultez [Wait Chain Traversal](/windows/desktop/Debug/wait-chain-traversal) (page éventuellement en anglais).|
|**Start Time**|Heure à laquelle la tâche est devenue active.|
|**Durée**|Nombre de secondes durant lesquelles la tâche a été active.|
|**Heure d'achèvement**|Heure à laquelle la tâche s’est terminée.|
|**Lieu**|Emplacement actuel dans la pile d’appels de la tâche. Pointez sur cette cellule pour visualiser l’ensemble de la pile des appels de la tâche. Les tâches planifiées ne disposent pas de valeur dans cette colonne.|
|**Tâche**|Méthode initiale et tous les arguments passés à la tâche lorsqu'elle a été créée.|
|**AsyncState**|En matière de code managé, état de la tâche. Par défaut, cette colonne est masquée. Pour afficher cette colonne, ouvrez le menu contextuel pour l'une des en-têtes de colonnes. Sélectionnez **Colonnes**, **AsyncState**.|
|**Parent**|ID de la tâche qui a créé cette tâche. Si rien n’est indiqué, la tâche n’a aucun parent. Ceci s'applique uniquement aux programmes gérés.|
|**Assignation de thread**|ID et nom du thread sur lequel la tâche s'exécute.|
|**AppDomain**|Pour du code managé, domaine d’application dans lequel la tâche s’exécute.|
|**task_group**|Pour du code natif, adresse de l’objet [task_group](/cpp/parallel/concrt/reference/task-group-class) qui a planifié la tâche. Pour les agents asynchrones et les tâches légères, cette colonne a la valeur 0.|
|**Processus**|ID du processus que la tâche exécute.|

 Vous pouvez ajouter des colonnes à la vue en cliquant avec le bouton droit sur un en-tête de colonne et en sélectionnant ensuite les colonnes souhaitées. (Supprimer les colonnes en effaçant les sélections.) Vous pouvez également réorganiser les colonnes en les faisant glisser vers la gauche ou vers la droite. Le menu contextuel des colonnes est présenté dans l'illustration suivante.

 ![Menu du mode raccourci dans la fenêtre tâches](../debugger/media/parallel_tasks_contextmenu.png "Parallel_Tasks_ContextMenu")

## <a name="sorting-tasks"></a>Tri de tâches
 Pour trier des tâches en fonction des critères de colonne, cliquez sur l’en-tête d’une colonne. Par exemple, en cliquant sur l’en-tête de colonne **ID** , vous pouvez trier les tâches par ID de tâche : 1, 2, 3, 4, 5, etc. Pour inverser l'ordre de tri, cliquez à nouveau sur l'en-tête de la colonne. La colonne et l'ordre de tri actuels sont indiqués par une flèche dans la colonne.

## <a name="grouping-tasks"></a>Regroupement de tâches
 Vous pouvez regrouper des tâches en fonction d’une colonne de la vue Liste. Ainsi, lorsque vous cliquez avec le bouton droit sur l’en-tête de colonne **État** et que vous cliquez ensuite sur **Grouper par** > **[*état*]**, vous pouvez regrouper toutes les tâches possédant le même état. Par exemple, vous pouvez voir rapidement les tâches en attente afin de vous concentrer sur la raison pour laquelle elles sont bloquées. Vous pouvez également réduire un groupe qui ne présente pas d‘intérêt pour la session de débogage. De la même manière, vous pouvez regrouper les tâches en fonction des autres colonnes. Pour ajouter un indicateur à un groupe (ou en supprimer un), il suffit de cliquer sur le bouton en regard de l'en-tête de groupe. L’illustration suivante présente la fenêtre **Tâches** en mode regroupé.

 ![Mode groupé dans la fenêtre tâches](../debugger/media/parallel_tasks_groupedmode.png "Parallel_Tasks_GroupedMode")

## <a name="parent-child-view"></a>Vue Parent enfant
 (Cette vue est disponible uniquement pour le code managé.) En cliquant avec le bouton droit sur l’en-tête de colonne **État** , puis en cliquant sur **regrouper par**  >  **parent**, vous pouvez modifier la liste des tâches en vue hiérarchique, dans laquelle chaque tâche enfant est un sous-nœud qui peut être affiché ou masqué sous son parent.

## <a name="flagging-tasks"></a>Ajout d'indicateurs à des tâches
 Vous pouvez marquer le thread sur lequel une tâche s’exécute en sélectionnant l’élément de la liste des tâches, puis en choisissant **marquer le thread affecté** dans le menu contextuel, ou en cliquant sur l’icône d’indicateur dans la première colonne. Si vous signalez plusieurs tâches, vous pouvez ensuite effectuer un tri sur la colonne d'indicateur pour déplacer toutes les tâches avec indicateur vers le haut afin de pouvoir vous concentrer uniquement sur celles-ci. Vous pouvez également utiliser la fenêtre **Piles parallèles** pour afficher uniquement les tâches avec indicateur. Cela vous permet d'éliminer par filtrage les tâches qui ne vous intéressent pas pour le débogage. Les indicateurs ne sont pas persistants entre les sessions de débogage.

## <a name="freezing-and-thawing-tasks"></a>Gel et libération des tâches
 Vous pouvez geler le thread sur lequel une tâche s’exécute en cliquant avec le bouton droit sur la tâche, puis en cliquant sur **Verrouiller le thread affecté**. (Si une tâche est déjà gelée, la commande est **libérer le thread affecté**.) Quand vous figez un thread, ce thread ne s’exécute pas lorsque vous exécutez le code pas à pas après le point d’arrêt actuel. L’option **figer tous les threads mais cette** commande gèle tous les threads sauf celui qui exécute l’élément de la liste des tâches.

 L’illustration suivante présente les autres éléments de menu pour chaque tâche.

 ![Menu du thread de raccourci dans la fenêtre tâches](../debugger/media/parallel_tasks_contextmenu2.png "Parallel_Tasks_ContextMenu2")

## <a name="switching-the-active-task-or-frame"></a>Basculement de la tâche ou du frame actif

La commande **basculer vers** la tâche transforme la tâche active en tâche active. La commande **basculer vers le frame** fait du frame de pile sélectionné le frame de pile actif. Le contexte du débogueur bascule vers la tâche actuelle ou le frame de pile sélectionné.

## <a name="see-also"></a>Voir aussi

- [Présentation du débogueur](../debugger/debugger-feature-tour.md)
- [Débogage du code managé](../debugger/debugging-managed-code.md)
- [Programmation parallèle](/dotnet/standard/parallel-programming/index)
- [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime)
- [Utilisation de la fenêtre Piles parallèles](../debugger/using-the-parallel-stacks-window.md)
- [Procédure pas à pas : débogage d’une application parallèle](../debugger/walkthrough-debugging-a-parallel-application.md)