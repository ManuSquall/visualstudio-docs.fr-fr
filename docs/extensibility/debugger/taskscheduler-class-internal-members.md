---
title: TaskScheduler, classe-membres internes | Microsoft Docs
description: Découvrez les membres internes de la classe System. Threading. Tasks. TaskScheduler qui vous aideront à implémenter un débogueur personnalisé.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10528e57137f8605e7f140d4ab8d4a3399029a5f
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996004"
---
# <a name="taskscheduler-class---internal-members"></a>TaskScheduler, classe-membres internes
Cet article décrit les membres internes de la <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> classe qui vous aident à implémenter un débogueur personnalisé. Pour obtenir des informations générales sur cette classe, consultez l' <xref:System.Threading.Tasks.TaskScheduler> article de référence.

 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly :** mscorlib (en *mscorlib.dll*)

 Étant donné que vous ne pouvez pas accéder à ces membres internes à partir du .NET Framework, la syntaxe suivante est fournie en Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler
       extends System.Object
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|Nom|Description|
|----------|-----------------|
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Récupère un tableau de toutes les tâches planifiées.|
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Récupère un tableau de tous les <xref:System.Threading.Tasks.TaskScheduler> objets qui sont actuellement actifs.|

## <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Éléments internes de l’extension parallèle pour le .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
