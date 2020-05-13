---
title: CONST_GUID_ARRAY Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONST_GUID_ARRAY
helpviewer_keywords:
- CONST_GUID_ARRAY structure
ms.assetid: bd55e7d8-372c-4c3e-9eed-28f6b415a5db
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c0021ef24e0cafec0119263d2c74175f0d38d784
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737634"
---
# <a name="const_guid_array"></a>CONST_GUID_ARRAY
Une structure qui contient `GUID`une liste de s.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct tagCONST_GUID_ARRAY {
    DWORD       dwCount;
    CONST GUID* Members;
} CONST_GUID_ARRAY;
```

```csharp
public struct CONST_GUID_ARRAY {
    public uint   dwCount;
    public Guid[] Members;
}
```

## <a name="members"></a>Membres
`dwCount`\
Nombre `GUID`de s `Members` dans le tableau.

`Members`\
Array `GUID`de s.

## <a name="remarks"></a>Notes
Cette structure est transmise à la méthode [PublishProgram,](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) et est retournée des méthodes [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) et [WatchForProviderEvents.](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)

Le propriétaire d’une instance de cette structure est responsable de la libération de toute mémoire allouée.

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)
