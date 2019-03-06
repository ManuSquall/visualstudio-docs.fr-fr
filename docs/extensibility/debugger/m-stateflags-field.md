---
title: Champ m_stateFlags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateFlags field, Task class [.NET Framework debug engines]
ms.assetid: 82b20efc-08f2-4cd2-91f6-4e01e3da906b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6766fa98d6141005ed88d623ef8608035593a2a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704590"
---
# <a name="mstateflags-field"></a>champ m_stateFlags
Stocke des informations sur l’état actuel de la <xref:System.Threading.Tasks.Task> objet.

 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly :** mscorlib (dans *mscorlib.dll*)

 Étant donné que vous ne pouvez pas accéder à ce membre interne du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.field assembly int32 modreq(System.Runtime.CompilerServices.IsVolatile) m_stateFlags
```

## <a name="remarks"></a>Notes
 Vous utilisez généralement le <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=fullName> propriété pour accéder à cette valeur.

 Ce membre peut être n’importe quelle combinaison des valeurs suivantes :

-   [TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)

-   [TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)

-   [TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)

-   [TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)

-   [TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)

## <a name="see-also"></a>Voir aussi
- [Classe Task](../../extensibility/debugger/task-class-internal-members.md)