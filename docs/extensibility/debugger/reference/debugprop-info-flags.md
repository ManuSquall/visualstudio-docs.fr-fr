---
title: DEBUGPROP_INFO_FLAGS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa7e4a498188dc91f2a47b3ccf27f367f15ec77b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737397"
---
# <a name="debugprop_info_flags"></a>DEBUGPROP_INFO_FLAGS
Précise les informations à récupérer sur un objet de propriété débogé.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
typedef DWORD DEBUGPROP_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
```

## <a name="fields"></a>Champs
`DEBUGPROP_INFO_FULLNAME`\
Initialiser/utiliser `bstrFullName` le champ.

`DEBUGPROP_INFO_NAME`\
Initialiser/utiliser `bstrName` le champ.

`DEBUGPROP_INFO_TYPE`\
Initialiser/utiliser `bstrType` le champ.

`DEBUGPROP_INFO_VALUE`\
Initialiser/utiliser `bstrValue` le champ.

`DEBUGPROP_INFO_ATTRIB`\
Initialiser/utiliser `dwAttrib` le champ.

`DEBUGPROP_INFO_PROP`\
Initialiser/utiliser `pProperty` le champ qui contient une interface [IDebugProperty2.](../../../extensibility/debugger/reference/idebugproperty2.md)

`DEBUGPROP_INFO_VALUE_AUTOEXPAND`\
Précise que le champ de valeur doit contenir la valeur auto-élargie, si disponible, pour ce type d’objet.

`DEBUGPROP_INFO_VALUE_NOFUNCEVAL`\
Action déconseillée.

`DEBUGPROP_INFO_VALUE_RAW`\
Ne retournez aucune valeur ou membre embelli (c’est-à-dire ne formatez pas les valeurs).

`DEBUGPROP_INFO_VALUE_NO_TOSTRING`\
Ne retournez pas de valeurs synthétisées `ToString()` spéciales (par exemple, ne faites pas appel à un objet pour produire une valeur).

`DEBUGPROP_INFO_NONE`\
Spécifie qu'aucun indicateur n'est défini.

`DEBUGPROP_INFO_STANDARD`\
Initialiser / `dwAttrib`utiliser `bstrName` `bstrType`le `bstrValue` , , , et les champs.

`DEBUGPROP_INFO_All`\
Indique un masque de tous les drapeaux.

## <a name="remarks"></a>Notes
Ces valeurs sont transmises aux méthodes [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)et [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) pour indiquer quels champs doivent être parasésés la structure [DEBUG_PROPERTY_INFO.](../../../extensibility/debugger/reference/debug-property-info.md)

Ces valeurs sont également `dwFields` utilisées `DEBUG_PROPERTY_INFO` pour le membre de la structure pour indiquer quels champs de la structure sont utilisés et valides lorsque la structure est retournée.

Ces valeurs peuvent être combinées avec un peu plus. `OR`

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo (en anglais)](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
