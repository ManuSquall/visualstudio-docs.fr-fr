---
title: CONTEXT_INFO_FIELDS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b398e7ee549026750cbdff7b7fede8522116f346
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737593"
---
# <a name="context_info_fields"></a>CONTEXT_INFO_FIELDS
Précise les informations à récupérer sur un contexte de mémoire.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
typedef DWORD CONTEXT_INFO_FIELDS;
```

```csharp
public enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
```

## <a name="fields"></a>Champs
`CIF_MODULEURL`\
Initialiser/utiliser `bstrModuleUrl` le champ de la structure [CONTEXT_INFO.](../../../extensibility/debugger/reference/context-info.md)

`CIF_FUNCTION`\
Initialiser/utiliser `bstrFunction` le champ `CONTEXT_INFO` de la structure.

`CIF_FUNCTIONOFFSET`\
Initialiser/utiliser `posFunctionOffset` le champ `CONTEXT_INFO` de la structure.

`CIF_ADDRESS`\
Initialiser/utiliser `bstrAddress` le champ `CONTEXT_INFO` de la structure.

`CIF_ADDRESSOFFSET`\
Initialiser/utiliser `bstrAddressOffset` le champ `CONTEXT_INFO` de la structure.

`CIF_ALLFIELDS`\
Initialiser/utiliser tous les `CONTEXT_INFO` champs de la structure.

## <a name="remarks"></a>Notes
Ces valeurs sont transmises à la méthode [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) pour indiquer quels champs de la structure [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) doivent être parasés.

Ces drapeaux sont également utilisés pour `CONTEXT_INFO` indiquer quels champs de la structure sont utilisés et valides lorsque la structure est retournée.

Ces valeurs peuvent être combinées avec un peu plus ou.

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
