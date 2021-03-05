---
description: Spécifie comment interpréter le type d’un objet IDebugField.
title: dwTYPE_KIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f51a84951cdfe09e13454035c3219324e9a68368
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170326"
---
# <a name="dwtype_kind"></a>dwTYPE_KIND
Spécifie comment interpréter le type d’un objet [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .

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
L’Union de [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) doit être interprétée comme une structure de [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) .

`TYPE_KIND_PDB`\
L' `TYPE_INFO` Union doit être interprétée comme une structure de [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) .

`TYPE_KIND_BUILT`\
L' `TYPE_INFO` Union doit être interprétée comme une structure de [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) .

## <a name="remarks"></a>Notes
Les valeurs de cette énumération apparaissent dans le `dwKind` champ de la structure [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) et sont utilisées pour déterminer comment interpréter le `type` membre Union. La `TYPE_INFO` structure est retournée par un appel à la méthode [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) .

## <a name="requirements"></a>Configuration requise
En-tête : SH. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
