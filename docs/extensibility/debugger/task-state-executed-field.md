---
title: TASK_STATE_EXECUTED Field ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_EXECUTED field, Task class [.NET Framework debug engines]
ms.assetid: 75b8f9d0-b908-40d0-b109-70feaed2ab0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa637b8bc29f53ca6dde1b13310d83a5e176408f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712697"
---
# <a name="task_state_executed-field"></a>champ TASK_STATE_EXECUTED
La tâche est en cours d'exécution mais n'est pas encore terminée.

 **Espace nom:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Assemblée:** mscorlib (en mscorlib.dll)

 Parce que vous ne pouvez pas accéder à ce membre interne à partir du cadre .NET, la syntaxe suivante est fournie dans common Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.field static assembly literal int32 TASK_STATE_EXECUTED = int32(0x00020000)
```

## <a name="remarks"></a>Notes
 Si le champ [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) contient cette <xref:System.Threading.Tasks.Task.Status%2A> valeur, <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>la propriété revient .

## <a name="see-also"></a>Voir aussi
- [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
