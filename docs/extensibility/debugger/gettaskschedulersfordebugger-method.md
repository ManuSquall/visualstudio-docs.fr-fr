---
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
ms.openlocfilehash: 2b9826681d2d322b1b240abb4062de007b564619
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921269"
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

## <a name="return-value"></a>Valeur de retour
 Tableau de tous les <xref:System.Threading.Tasks.TaskScheduler> objets actuellement actifs dans ce <xref:System.AppDomain> .

## <a name="remarks"></a>Remarques
 Cette méthode n’est pas thread-safe et vous ne devez pas l’utiliser simultanément avec d’autres instances de <xref:System.Threading.Tasks.TaskScheduler> . Appelez cette méthode à partir d’un débogueur uniquement lorsque le débogueur a suspendu tous les autres threads.

## <a name="see-also"></a>Voir aussi
- [TaskScheduler (classe)](../../extensibility/debugger/taskscheduler-class-internal-members.md)
