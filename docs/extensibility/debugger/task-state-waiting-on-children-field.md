---
title: TASK_STATE_WAITING_ON_CHILDREN Field ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_WAITING_ON_CHILDREN field, Task class [.NET Framework debug engines]
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 27b9963db54d939b3d509da451478c20dbe0e7d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712585"
---
# <a name="task_state_waiting_on_children-field"></a>champ TASK_STATE_WAITING_ON_CHILDREN
La tâche a fini d’exécuter son délégué et attend implicitement que les tâches des enfants attachés se terminent.

 **Espace nom:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Assemblée:** mscorlib (en *mscorlib.dll*)

 Parce que vous ne pouvez pas accéder à ce membre interne à partir du cadre .NET, la syntaxe suivante est fournie dans common Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)
```

## <a name="remarks"></a>Notes
 Si le champ [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) contient cette <xref:System.Threading.Tasks.Task.Status%2A> valeur, <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>la propriété revient .

## <a name="see-also"></a>Voir aussi
- [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
