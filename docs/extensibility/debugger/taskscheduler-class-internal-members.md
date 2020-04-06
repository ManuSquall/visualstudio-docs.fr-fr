---
title: Classe TaskScheduler - Membres internes Microsoft Docs
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
ms.openlocfilehash: a53abc8b24edb06445c23c19744d00d50de8735d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712564"
---
# <a name="taskscheduler-class---internal-members"></a>Classe TaskScheduler - Membres internes
Cet article décrit les membres <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> internes de la classe qui vous aident à mettre en œuvre un débbugger personnalisé. Pour plus d’informations générales <xref:System.Threading.Tasks.TaskScheduler> sur cette classe, voir l’article de référence.

 **Espace nom:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Assemblée:** mscorlib (en *mscorlib.dll*)

 Parce que vous ne pouvez pas accéder à ces membres internes à partir du cadre .NET, la syntaxe suivante est fournie dans common Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler
       extends System.Object
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|Nom|Description|
|----------|-----------------|
|[GetScheduledTasksForDebugger GetScheduledTasksForDebugger GetScheduledTasksForDebugger GetS](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Récupère un éventail de toutes les tâches prévues.|
|[GetTaskSchedulersForDebugger GetTaskSchedulersForDebugger GetTaskSchedulersForDebugger GetTa](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Récupère une gamme <xref:System.Threading.Tasks.TaskScheduler> de tous les objets qui sont actuellement actifs.|

## <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Internals d’extension parallèle pour le cadre .NET](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
