---
description: Stocke les informations relatives à l’état actuel de l’objet System. Threading. Tasks. Task.
title: Champ m_stateFlags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateFlags field, Task class [.NET Framework debug engines]
ms.assetid: 82b20efc-08f2-4cd2-91f6-4e01e3da906b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5df101d0c75ad7bd2a12393c4440c7dcd5484656
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059663"
---
# <a name="m_stateflags-field"></a>champ m_stateFlags
Stocke les informations sur l’état actuel de l' <xref:System.Threading.Tasks.Task> objet.

 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly :** mscorlib (en *mscorlib.dll*)

 Étant donné que vous ne pouvez pas accéder à ce membre interne à partir de la .NET Framework, la syntaxe suivante est fournie en Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.field assembly int32 modreq(System.Runtime.CompilerServices.IsVolatile) m_stateFlags
```

## <a name="remarks"></a>Notes
 En général, vous utilisez la <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=fullName> propriété pour accéder à cette valeur.

 Ce membre peut être n’importe quelle combinaison des valeurs suivantes :

- [TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)

- [TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)

- [TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)

- [TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)

- [TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)

## <a name="see-also"></a>Voir aussi
- [Classe de tâche](../../extensibility/debugger/task-class-internal-members.md)
