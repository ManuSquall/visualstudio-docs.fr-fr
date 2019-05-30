---
title: dwTYPE_KIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 12fe23d53939303be6b7e6a20ff12d2524d71593
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318123"
---
# <a name="dwtypekind"></a>dwTYPE_KIND
Spécifie comment interpréter le type d’un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objet.

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
Le [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) union doit être interprétée comme un [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) structure.

`TYPE_KIND_PDB`\
Le `TYPE_INFO` union doit être interprétée comme un [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) structure.

`TYPE_KIND_BUILT`\
Le `TYPE_INFO` union doit être interprétée comme un [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) structure.

## <a name="remarks"></a>Notes
Les valeurs de cette énumération s’affichent dans le `dwKind` champ la [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) structurer et sont utilisées pour déterminer comment interpréter le `type` membre d’union. Le `TYPE_INFO` structure est retournée par un appel à la [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) (méthode).

## <a name="requirements"></a>Configuration requise
En-tête : sh.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
