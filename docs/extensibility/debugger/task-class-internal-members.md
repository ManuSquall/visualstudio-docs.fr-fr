---
title: Classe de tâches - Membres internes Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcf278c0248b344cea4be7cf161ecc91581f5f2e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712733"
---
# <a name="task-class---internal-members"></a>Classe de tâches - membres internes
Cet article décrit les membres <xref:System.Threading.Tasks.Task?displayProperty=fullName> internes de la classe qui vous aident à mettre en œuvre un débbugger personnalisé. Pour plus d’informations générales <xref:System.Threading.Tasks.Task> sur cette classe, voir l’article de référence.

 **Espace nom:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Assemblée:** mscorlib (en *mscorlib.dll*)

 Parce que vous ne pouvez pas accéder à ces membres internes à partir du cadre .NET, la syntaxe suivante est fournie dans common Intermediate Language (CIL).

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
|[Méthode SetNotificationForWaitCompletion](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Définit ou efface le TASK_STATE_WAIT_COMPLETION_NOTIFICATION’état bit.|
|[Méthode NotifyDebuggerOfWaitCompletion](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Méthode de la placeholder utilisée comme cible de point d’arrêt par le débruceur.|

### <a name="fields"></a>Champs

|Nom|Description|
|----------|-----------------|
|[m_action](../../extensibility/debugger/m-action-field.md)|Le délégué qui représente le <xref:System.Threading.Tasks.Task> code à exécuter dans l’objet.|
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Stocke des <xref:System.Threading.Tasks.Task> propriétés supplémentaires de l’objet.|
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Le champ d’appui pour la <xref:System.Threading.Tasks.Task?displayProperty=fullName> propriété mère.|
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Stocke des informations sur <xref:System.Threading.Tasks.Task> l’état actuel de l’objet.|
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Un objet qui représente les données qui seront utilisées par l’action.|
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Le champ d’appui pour la <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> propriété.|
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|Le prochain identifiant <xref:System.Threading.Tasks.Task> disponible pour un objet.|
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Indique que la tâche annulée avant d’atteindre l’état de fonctionnement, ou que la tâche a confirmé son annulation et complétée sans exception.|
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Indique que la tâche est en cours d’exécution.|
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Indique que la tâche a été accomplie en raison d’une exception non gérée.|
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Indique que la tâche terminée avec succès.|
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Indique que la tâche a fini d’exécuter son délégué et attend implicitement la fin des tâches d’enfants attachés.|

## <a name="remarks"></a>Notes
 Les méthodes internes suivantes sont utiles à un moteur <xref:System.Threading.Tasks.Task> de débogénaire car elles marquent l’entrée à l’exécution du code :

- `Execute`

- `ExecuteEntry`

- `ExecuteWithThreadLocal`

- `Finish`

- `InnerInvoke`

- `InternalWait`

## <a name="see-also"></a>Voir aussi
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- [Internals d’extension parallèle pour le cadre .NET](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
