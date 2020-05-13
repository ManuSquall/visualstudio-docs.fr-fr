---
title: PDB_TYPE Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f736d7d9b190fc46945e2f4f7c309b88c3e851f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714106"
---
# <a name="pdb_type"></a>PDB_TYPE

Cette structure spécifie des informations sur un type de champ tiré d’un symbole PDB.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _tagTYPE_PDB {
    ULONG32 ulAppDomainID;
    GUID    guidModule;
    DWORD   symid;
} PDB_TYPE;
```

```csharp
public struct PDB_TYPE {
    public uint ulAppDomainID;
    public Guid guidModule;
    public uint symid;
};
```

## <a name="members"></a>Membres

`ulAppDomainID`\
ID de l’application à partir de laquelle le symbole est venu. Ceci est utilisé pour identifier de façon unique un exemple de l’application.

`guidModule`\
Le GUID du module qui contient ce champ.

`symid`\
L’ID du symbole qui correspond à ce champ.

## <a name="remarks"></a>Notes

Cette structure fait partie du [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) syndicat dans la structure `dwKind` TYPE_INFO `TYPE_INFO` lorsque le `TYPE_KIND_PDB` champ de la structure est fixé à (une valeur de [l’dwTYPE_KIND’énumération).](../../../extensibility/debugger/reference/dwtype-kind.md)

## <a name="requirements"></a>Spécifications

En-tête: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi

- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
