---
title: M_stateFlags Field ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateFlags field, Task class [.NET Framework debug engines]
ms.assetid: 82b20efc-08f2-4cd2-91f6-4e01e3da906b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b504d134c8951072795dc2e202cf05082b12cb64
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738388"
---
# <a name="m_stateflags-field"></a>champ m_stateFlags
Stocke des informations sur <xref:System.Threading.Tasks.Task> l’état actuel de l’objet.

 **Espace nom:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Assemblée:** mscorlib (en *mscorlib.dll*)

 Parce que vous ne pouvez pas accéder à ce membre interne à partir du cadre .NET, la syntaxe suivante est fournie dans common Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.field assembly int32 modreq(System.Runtime.CompilerServices.IsVolatile) m_stateFlags
```

## <a name="remarks"></a>Notes
 Vous utilisez <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=fullName> généralement la propriété pour accéder à cette valeur.

 Ce membre peut être n’importe quelle combinaison des valeurs suivantes :

- [TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)

- [TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)

- [TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)

- [TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)

- [TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)

## <a name="see-also"></a>Voir aussi
- [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
