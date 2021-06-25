---
description: Cette rubrique décrit les membres internes de la classe System. Runtime. CompilerServices. AsyncTaskMethodBuilder.
title: '&lt;Structure TResult AsyncTaskMethodBuilder &gt; -membres internes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ca9d5ccfcd5870902cc40a623aabb93a3115f469
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903799"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>&lt;Structure TResult AsyncTaskMethodBuilder &gt; -membres internes
Cette rubrique décrit les membres internes de la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> classe. Pour obtenir des informations générales sur cette classe, consultez la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> rubrique de référence.

 **Espace de noms :** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Assembly :** mscorlib (en mscorlib.dll)

 Étant donné que vous ne pouvez pas accéder à ces membres internes à partir du .NET Framework, la syntaxe suivante est fournie en Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Membres internes

|Nom|Description|
|----------|-----------------|
|[Propriété ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Obtient un objet qui peut être utilisé pour identifier de manière unique ce générateur auprès du débogueur.|
|[champ m_task](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Représente la tâche générée initialisée tardivement.|

## <a name="see-also"></a>Voir aussi
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>
- [Éléments internes de l’extension parallèle pour le .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
