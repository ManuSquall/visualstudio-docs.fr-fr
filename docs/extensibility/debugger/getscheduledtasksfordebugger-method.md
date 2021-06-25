---
description: Récupère un tableau de toutes les tâches planifiées.
title: Méthode GetScheduledTasksForDebugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 51da481edb636450770d0cff569b9ef411e17cf6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900952"
---
# <a name="getscheduledtasksfordebugger-method"></a>Méthode GetScheduledTasksForDebugger
Récupère un tableau de toutes les tâches planifiées.

 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly :** mscorlib (en *mscorlib.dll*)

 Étant donné que vous ne pouvez pas accéder à ce membre interne à partir de la .NET Framework, la syntaxe suivante est fournie en Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed
```

## <a name="return-value"></a>Valeur de retour
 Tableau de toutes les tâches planifiées. Chaque tâche est en cours d’exécution ou a terminé son exécution.

## <a name="remarks"></a>Remarques
 Cette méthode n’est pas thread-safe et vous ne devez pas l’utiliser simultanément avec d’autres instances de <xref:System.Threading.Tasks.TaskScheduler> . Appelez cette méthode à partir d’un débogueur uniquement lorsque le débogueur a suspendu tous les autres threads.

## <a name="see-also"></a>Voir aussi
- [TaskScheduler (classe)](../../extensibility/debugger/taskscheduler-class-internal-members.md)
