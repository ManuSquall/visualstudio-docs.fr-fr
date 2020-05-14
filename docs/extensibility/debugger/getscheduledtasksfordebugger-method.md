---
title: Méthode GetScheduledTasksForDebugger (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fca6c8e92cd0b4755bd79b8e142a7e1d283f868d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738663"
---
# <a name="getscheduledtasksfordebugger-method"></a>Méthode GetScheduledTasksForDebugger
Récupère un éventail de toutes les tâches prévues.

 **Espace nom:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Assemblée:** mscorlib (en *mscorlib.dll*)

 Parce que vous ne pouvez pas accéder à ce membre interne à partir du cadre .NET, la syntaxe suivante est fournie dans common Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed
```

## <a name="return-value"></a>Valeur de retour
 Un éventail de toutes les tâches prévues. Chaque tâche est l’exécution ou a fini l’exécution.

## <a name="remarks"></a>Notes
 Cette méthode n’est pas sans danger de thread et <xref:System.Threading.Tasks.TaskScheduler>vous ne devriez pas l’utiliser en même temps que d’autres cas de . Appelez cette méthode à partir d’un débbugger seulement lorsque le débbuggeur a suspendu tous les autres threads.

## <a name="see-also"></a>Voir aussi
- [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)
