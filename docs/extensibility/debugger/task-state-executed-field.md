---
description: La tâche est en cours d'exécution mais n'est pas encore terminée.
title: Champ TASK_STATE_EXECUTED | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TASK_STATE_EXECUTED field, Task class [.NET Framework debug engines]
ms.assetid: 75b8f9d0-b908-40d0-b109-70feaed2ab0c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ca0d2f578cc4e20b71e562d5b82245995bfd2969
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902850"
---
# <a name="task_state_executed-field"></a>Champ TASK_STATE_EXECUTED
La tâche est en cours d'exécution mais n'est pas encore terminée.

 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly :** mscorlib (en mscorlib.dll)

 Étant donné que vous ne pouvez pas accéder à ce membre interne à partir de la .NET Framework, la syntaxe suivante est fournie en Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.field static assembly literal int32 TASK_STATE_EXECUTED = int32(0x00020000)
```

## <a name="remarks"></a>Notes
 Si le champ [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) contient cette valeur, la <xref:System.Threading.Tasks.Task.Status%2A> propriété retourne <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>Voir aussi
- [Classe de tâche](../../extensibility/debugger/task-class-internal-members.md)
