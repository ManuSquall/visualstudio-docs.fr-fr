---
title: BPERESI_FIELDS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: af2f20e7d3abd79261dc18753a7eb940666fc186
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737769"
---
# <a name="bperesi_fields"></a>BPERESI_FIELDS
Spécifie les informations à récupérer au sujet d’une résolution ratée d’un point d’arrêt.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
typedef DWORD BPERESI_FIELDS;
```

```csharp
public enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>Champs
`PERESI_BPRESLOCATION`\
Initialiser/utiliser `bpResLocation` le champ (emplacement de résolution de point de rupture) de la structure [BP_ERROR_RESOLUTION_INFO.](../../../extensibility/debugger/reference/bp-error-resolution-info.md)

`BPERESI_PROGRAM`\
Initialiser/utiliser `pProgram` le champ `BP_ERROR_RESOLUTION_INFO` de la structure.

`BPERESI_THREAD`\
Initialiser/utiliser `pThread` le champ `BP_ERROR_RESOLUTION_INFO` de la structure.

`BPERESI_MESSAGE`\
Initialiser/utiliser `bstrMessage` le champ `BP_ERROR_RESOLUTION_INFO` de la structure.

`BPERESI_TYPE`\
Initialiser/utiliser `dwType` le champ (type de `BP_ERROR_RESOLUTION_INFO` point d’arrêt) de la structure.

`BPERESI_ALLFIELDS`\
Initialiser/utiliser tous les `BP_ERROR_RESOLUTION_INFO` champs de la structure.

## <a name="remarks"></a>Notes
Passé comme paramètre à la méthode [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) pour indiquer quels champs de la structure [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) doivent être parasélisés.

Ces valeurs sont également utilisées pour `BP_ERROR_RESOLUTION_INFO` indiquer quels champs de la structure sont utilisés et valides lorsque cette structure est retournée.

Ces valeurs peuvent être combinées avec un peu plus. `OR`

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
