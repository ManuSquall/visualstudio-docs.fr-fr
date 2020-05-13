---
title: GetTaskSchedulersForDebugger Méthode (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a3b0c8c16b10a4cf2268161d8a2db96c10303b1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738650"
---
# <a name="gettaskschedulersfordebugger-method"></a>Méthode GetTaskSchedulersForDebugger
Récupère une gamme <xref:System.Threading.Tasks.TaskScheduler> de tous les objets qui sont actuellement actifs.

 **Espace nom:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Assemblée:** mscorlib (en *mscorlib.dll*)

 Parce que vous ne pouvez pas accéder à ce membre interne à partir du cadre .NET, la syntaxe suivante est fournie dans common Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Valeur retournée
 Un tableau <xref:System.Threading.Tasks.TaskScheduler> de tous les objets <xref:System.AppDomain>qui sont actuellement actifs dans ce .

## <a name="remarks"></a>Notes
 Cette méthode n’est pas sans danger de thread et <xref:System.Threading.Tasks.TaskScheduler>vous ne devriez pas l’utiliser en même temps que d’autres cas de . Appelez cette méthode à partir d’un débbugger seulement lorsque le débbuggeur a suspendu tous les autres threads.

## <a name="see-also"></a>Voir aussi
- [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)
