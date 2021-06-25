---
title: Classe de tâche-membres internes | Microsoft Docs
description: Découvrez les membres internes de la classe System. Threading. Tasks. Task qui vous aideront à implémenter un débogueur personnalisé.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 37691714d0168594b61a1a3849f7b65264e9999e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902889"
---
# <a name="task-class---internal-members"></a>Classe de tâche-membres internes
Cet article décrit les membres internes de la <xref:System.Threading.Tasks.Task?displayProperty=fullName> classe qui vous aident à implémenter un débogueur personnalisé. Pour obtenir des informations générales sur cette classe, consultez l' <xref:System.Threading.Tasks.Task> article de référence.

 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly :** mscorlib (en *mscorlib.dll*)

 Étant donné que vous ne pouvez pas accéder à ces membres internes à partir du .NET Framework, la syntaxe suivante est fournie en Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.class public auto ansi System.Threading.Tasks.Task
       extends System.Object
       implements System.Threading.IThreadPoolWorkItem,
                  System.IAsyncResult,
                  System.IDisposable,
                  System.Threading.ICancelableOperation
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|Nom|Description|
|----------|-----------------|
|[Méthode SetNotificationForWaitCompletion](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Définit ou efface le bit d’État TASK_STATE_WAIT_COMPLETION_NOTIFICATION.|
|[Méthode NotifyDebuggerOfWaitCompletion](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Méthode d’espace réservé utilisée comme cible de point d’arrêt par le débogueur.|

### <a name="fields"></a>Champs

|Nom|Description|
|----------|-----------------|
|[m_action](../../extensibility/debugger/m-action-field.md)|Délégué qui représente le code à exécuter dans l' <xref:System.Threading.Tasks.Task> objet.|
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Stocke des propriétés supplémentaires de l' <xref:System.Threading.Tasks.Task> objet.|
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Champ de stockage de la <xref:System.Threading.Tasks.Task?displayProperty=fullName> propriété parente.|
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Stocke les informations sur l’état actuel de l' <xref:System.Threading.Tasks.Task> objet.|
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Objet qui représente les données qui seront utilisées par l’action.|
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Champ de stockage de la <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> propriété.|
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|Identificateur suivant disponible pour un <xref:System.Threading.Tasks.Task> objet.|
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Indique que la tâche a été annulée avant d’atteindre l’État en cours d’exécution, ou que la tâche a confirmé son annulation et s’est terminée sans exception.|
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Indique que la tâche est en cours d’exécution.|
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Indique que la tâche s’est terminée en raison d’une exception non gérée.|
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Indique que l’exécution de la tâche s’est terminée avec succès.|
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Indique que la tâche a terminé l’exécution de son délégué et qu’elle attend implicitement la fin des tâches enfants attachées.|

## <a name="remarks"></a>Remarques
 Les méthodes internes suivantes sont utiles à un moteur du débogueur, car elles marquent l’entrée pour <xref:System.Threading.Tasks.Task> l’exécution du code :

- `Execute`

- `ExecuteEntry`

- `ExecuteWithThreadLocal`

- `Finish`

- `InnerInvoke`

- `InternalWait`

## <a name="see-also"></a>Voir aussi
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- [Éléments internes de l’extension parallèle pour le .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
