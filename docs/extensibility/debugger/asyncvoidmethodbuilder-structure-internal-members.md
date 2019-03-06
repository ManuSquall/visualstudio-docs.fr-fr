---
title: Structure AsyncVoidMethodBuilder - membres internes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a4c51d76d38680945eaccbd3ace256813668c51
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56716803"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>Structure AsyncVoidMethodBuilder - membres internes
Cette rubrique décrit les membres internes de la <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> classe. Pour obtenir des informations générales sur cette classe, consultez le <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> rubrique de référence.

 **Espace de noms :** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Assembly :** mscorlib (dans mscorlib.dll)

 Étant donné que vous ne peut pas accéder à ces membres internes à partir de .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Membres internes

|Name|Description|
|----------|-----------------|
|[Propriété de ObjectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Obtient un objet qui peut être utilisé pour identifier de manière unique ce générateur au débogueur.|
|[champ de m_objectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Représente l’objet initialisée tardivement utilisé par le débogueur pour identifier de manière unique ce générateur.|

## <a name="see-also"></a>Voir aussi
- <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>
- [Mécanismes internes d’extension parallèle pour le .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)