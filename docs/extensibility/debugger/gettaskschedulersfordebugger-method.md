---
description: Récupère un tableau de tous les objets System. Threading. Tasks. TaskScheduler qui sont actuellement actifs.
title: Méthode GetTaskSchedulersForDebugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f60ffa851e8b8821e3d07e1bfdd6e864104b5001
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150092"
---
# <a name="gettaskschedulersfordebugger-method"></a>Méthode GetTaskSchedulersForDebugger
Récupère un tableau de tous les <xref:System.Threading.Tasks.TaskScheduler> objets qui sont actuellement actifs.

 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly :** mscorlib (en *mscorlib.dll*)

 Étant donné que vous ne pouvez pas accéder à ce membre interne à partir de la .NET Framework, la syntaxe suivante est fournie en Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Valeur renvoyée
 Tableau de tous les <xref:System.Threading.Tasks.TaskScheduler> objets actuellement actifs dans ce <xref:System.AppDomain> .

## <a name="remarks"></a>Notes
 Cette méthode n’est pas thread-safe et vous ne devez pas l’utiliser simultanément avec d’autres instances de <xref:System.Threading.Tasks.TaskScheduler> . Appelez cette méthode à partir d’un débogueur uniquement lorsque le débogueur a suspendu tous les autres threads.

## <a name="see-also"></a>Voir aussi
- [TaskScheduler (classe)](../../extensibility/debugger/taskscheduler-class-internal-members.md)
