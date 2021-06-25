---
description: L’exécution de la tâche s’est terminée avec succès.
title: Champ TASK_STATE_RAN_TO_COMPLETION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TASK_STATE_RAN_TO_COMPLETION field, Task class [.NET Framework debug engines]
ms.assetid: 0f4830af-fe0c-4141-b768-817f4e426b8c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4d168fe7e878471af4f70f2e58aab9748060c99e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902811"
---
# <a name="task_state_ran_to_completion-field"></a>Champ TASK_STATE_RAN_TO_COMPLETION
L’exécution de la tâche s’est terminée avec succès.

 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly :** mscorlib (en *mscorlib.dll*)

 Étant donné que vous ne pouvez pas accéder à ce membre interne à partir de la .NET Framework, la syntaxe suivante est fournie en Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.field static assembly literal int32 TASK_STATE_RAN_TO_COMPLETION = int32(0x02000000)
```

## <a name="remarks"></a>Notes
 Si le champ [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) contient cette valeur, la <xref:System.Threading.Tasks.Task.Status%2A> propriété retourne <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>Voir aussi
- [Classe de tâche](../../extensibility/debugger/task-class-internal-members.md)
