---
title: dwTYPE_KIND Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9d790f12d3fc21bbae7373470746af2ebfe6dc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737194"
---
# <a name="dwtype_kind"></a>dwTYPE_KIND
Précise comment interpréter le type d’objet [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};

typedef DWORD dwTYPE_KIND;
```

```csharp
public enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};
```

## <a name="fields"></a>Champs
`TYPE_KIND_METADATA`\
Le [syndicat TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) devrait être interprété comme une structure [METADATA_TYPE.](../../../extensibility/debugger/reference/metadata-type.md)

`TYPE_KIND_PDB`\
Le `TYPE_INFO` syndicat doit être interprété comme une structure [PDB_TYPE.](../../../extensibility/debugger/reference/pdb-type.md)

`TYPE_KIND_BUILT`\
Le `TYPE_INFO` syndicat doit être interprété comme une structure [BUILT_TYPE.](../../../extensibility/debugger/reference/built-type.md)

## <a name="remarks"></a>Notes
Les valeurs de ce recensement `dwKind` apparaissent dans le domaine de la structure [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) et `type` sont utilisées pour déterminer comment interpréter le membre du syndicat. La `TYPE_INFO` structure est retournée par un appel à la méthode [GetTypeInfo.](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)

## <a name="requirements"></a>Spécifications
En-tête: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [GetTypeInfo (en anglais)](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
