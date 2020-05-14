---
title: DEBUGREF_INFO_FLAGS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cb10ae5d3b4ce9f8aa777f643d412e075bd5293f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737387"
---
# <a name="debugref_info_flags"></a>DEBUGREF_INFO_FLAGS
Précise les informations à récupérer sur un objet de référence débogé.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
typedef DWORD DEBUGREF_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
```

## <a name="fields"></a>Champs
`DEBUGREF_INFO_NAME`\
Initialiser/utiliser `bstrName` le champ dans la structure.

`DEBUGREF_INFO_TYPE`\
Initialiser/utiliser `bstrType` le champ dans la structure.

`DEBUGREF_INFO_VALUE`\
Initialiser/utiliser `bstrValue` le champ dans la structure.

`DEBUGREF_INFO_ATTRIB`\
Initialiser/utiliser `dwAttrib` le champ dans la structure.

`DEBUGREF_INFO_REFTYPE`\
Initialiser/utiliser `dwRefType` le champ dans la structure.

`DEBUGREF_INFO_REF`\
Initialiser/utiliser `pReference` le champ dans la structure.

`DEBUGREF_INFO_VALUE_AUTOEXPAND`\
Le champ de valeur doit contenir la valeur auto-élargie, si disponible, pour ce type d’objet.

`DEBUGREF_INFO_NONE`\
Indique qu’aucun drapeau n’est fixé.

`DEBUGREF_INFO_ALL`\
Indique un masque des drapeaux.

## <a name="remarks"></a>Notes
Ces drapeaux sont transmis aux méthodes [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) et [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) pour indiquer quels champs de la structure [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) doivent être parasésés.

Utilisé pour `dwFields` le `DEBUG_REFERENCE_INFO` membre de la structure pour indiquer quels champs sont utilisés et valides lorsque la structure est retournée.

Ces valeurs peuvent être combinées avec un peu plus. `OR`

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
