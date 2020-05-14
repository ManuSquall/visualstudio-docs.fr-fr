---
title: Structure AsyncTaskMethodBuilder - Membres internes Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c918890551515ab9fadbf329d4c3ee96621c7aae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739377"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>Structure AsyncTaskMethodBuilder - membres internes
Ce sujet décrit les membres <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> internes de la classe. Pour plus d’informations générales <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> sur cette classe, consultez le sujet de référence.

 **Espace nom:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Assemblée:** mscorlib (en mscorlib.dll)

 Parce que vous ne pouvez pas accéder à ces membres internes à partir du cadre .NET, la syntaxe suivante est fournie dans common Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Membres internes

|Nom|Description|
|----------|-----------------|
|[ObjectIdForDebugger propriété](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Obtient un objet qui peut être utilisé pour identifier uniquement ce constructeur au débbugger.|
|[champ m_builder](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Représente l’objet de constructeur générique auquel cette instance non générique délègue des délégués.|

## <a name="see-also"></a>Voir aussi
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>
- [Internals d’extension parallèle pour le cadre .NET](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
