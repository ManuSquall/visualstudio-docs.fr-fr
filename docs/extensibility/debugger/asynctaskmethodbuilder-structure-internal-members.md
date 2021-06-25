---
description: Cet article décrit les membres internes de la classe System. Runtime. CompilerServices. AsyncTaskMethodBuilder.
title: Structure AsyncTaskMethodBuilder - Membres internes
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c5b21045688fc2be555c7a42d6e3b9014b66c761
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903838"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>Structure AsyncTaskMethodBuilder-membres internes
Cette rubrique décrit les membres internes de la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> classe. Pour obtenir des informations générales sur cette classe, consultez la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> rubrique de référence.

 **Espace de noms :** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Assembly :** mscorlib (en mscorlib.dll)

 Étant donné que vous ne pouvez pas accéder à ces membres internes à partir du .NET Framework, la syntaxe suivante est fournie en Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Membres internes

|Nom|Description|
|----------|-----------------|
|[Propriété ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Obtient un objet qui peut être utilisé pour identifier de manière unique ce générateur auprès du débogueur.|
|[champ m_builder](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Représente l’objet générateur générique auquel cette instance non générique délègue.|

## <a name="see-also"></a>Voir aussi
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>
- [Éléments internes de l’extension parallèle pour le .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
