---
title: Structure AsyncVoidMethodBuilder - Membres internes Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 866a53fae7bb2cc5325112b84d992da6f95af246
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739298"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>Structure AsyncVoidMethodBuilder - membres internes
Ce sujet décrit les membres <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> internes de la classe. Pour plus d’informations générales <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> sur cette classe, consultez le sujet de référence.

 **Espace nom:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Assemblée:** mscorlib (en mscorlib.dll)

 Parce que vous ne pouvez pas accéder à ces membres internes à partir du cadre .NET, la syntaxe suivante est fournie dans common Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Membres internes

|Nom|Description|
|----------|-----------------|
|[ObjectIdForDebugger propriété](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Obtient un objet qui peut être utilisé pour identifier uniquement ce constructeur au débbugger.|
|[champ m_objectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Représente l’objet paresseusement initialisé utilisé par le débbugeur pour identifier de façon unique ce constructeur.|

## <a name="see-also"></a>Voir aussi
- <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>
- [Internals d’extension parallèle pour le cadre .NET](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
