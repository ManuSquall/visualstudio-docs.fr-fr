---
title: AsyncTaskMethodBuilder&lt;TResult&gt; Structure - Membres internes Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c4f4da7070af09937af9e047ec83142584942e6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739336"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder&lt;TResult&gt; structure - membres internes
Ce sujet décrit les membres <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> internes de la classe. Pour plus d’informations générales <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> sur cette classe, consultez le sujet de référence.

 **Espace nom:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Assemblée:** mscorlib (en mscorlib.dll)

 Parce que vous ne pouvez pas accéder à ces membres internes à partir du cadre .NET, la syntaxe suivante est fournie dans common Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Membres internes

|Nom|Description|
|----------|-----------------|
|[ObjectIdForDebugger propriété](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Obtient un objet qui peut être utilisé pour identifier uniquement ce constructeur au débbugger.|
|[champ m_task](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Représente la tâche construite paresseusement paralysée.|

## <a name="see-also"></a>Voir aussi
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>
- [Internals d’extension parallèle pour le cadre .NET](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
