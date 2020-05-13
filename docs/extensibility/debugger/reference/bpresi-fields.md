---
title: BPRESI_FIELDS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 837bb7d25ab8dea2b146a98cc65d320b58162685
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737725"
---
# <a name="bpresi_fields"></a>BPRESI_FIELDS
Spécifie les informations à récupérer sur la résolution réussie d’un point d’arrêt.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
typedef DWORD BPRESI_FIELDS;
```

```csharp
public enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
```

## <a name="fields"></a>Champs
`BPRESI_BPRESLOCATION`\
Initialiser/utiliser `bpResLocation` le champ (emplacement de résolution de point de rupture) de la structure [BP_RESOLUTION_INFO.](../../../extensibility/debugger/reference/bp-resolution-info.md)

`BPRESI_PROGRAM`\
Initialiser/utiliser `pProgram` le champ `BP_RESOLUTION_INFO` de la structure.

`BPRESI_THREAD`\
Initialiser/utiliser `pThread` le champ `BP_RESOLUTION_INFO` de la structure.

`BPRESI_ALLFIELDS`\
Spécifie tous les champs.

## <a name="remarks"></a>Notes
Passé à la méthode [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) pour indiquer quels champs de la structure [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) doivent être parasélisés.

Ces drapeaux sont également utilisés pour `BP_RESOLUTION_INFO` indiquer quels champs de la structure sont utilisés et valides lorsque cette structure est retournée.

Ces valeurs peuvent être combinées avec un peu plus. `OR`

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
