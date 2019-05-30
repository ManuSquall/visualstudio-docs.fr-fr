---
title: Méthode GetScheduledTasksForDebugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49a63462eece9bef09579c7284f72790a3914bc2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353729"
---
# <a name="getscheduledtasksfordebugger-method"></a>Méthode GetScheduledTasksForDebugger
Récupère un tableau de toutes les tâches planifiées.

 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly :** mscorlib (dans *mscorlib.dll*)

 Étant donné que vous ne pouvez pas accéder à ce membre interne du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed
```

## <a name="return-value"></a>Valeur de retour
 Tableau de toutes les tâches planifiées. Chaque tâche s’exécute ou l’exécution est terminée.

## <a name="remarks"></a>Notes
 Cette méthode n’est pas thread-safe et vous ne devez pas l’utiliser en même temps que d’autres instances de <xref:System.Threading.Tasks.TaskScheduler>. Appelez cette méthode à partir d’un débogueur uniquement lorsque le débogueur a suspendu tous les autres threads.

## <a name="see-also"></a>Voir aussi
- [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)