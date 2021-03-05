---
description: Spécifie les informations à récupérer sur un objet de propriété de débogage.
title: DEBUGPROP_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63467e93b80648e6a00728dc66971b7c9b3c9b24
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170521"
---
# <a name="debugprop_info_flags"></a>DEBUGPROP_INFO_FLAGS
Spécifie les informations à récupérer sur un objet de propriété de débogage.

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
Initialiser/utiliser le `bstrFullName` champ.

`DEBUGPROP_INFO_NAME`\
Initialiser/utiliser le `bstrName` champ.

`DEBUGPROP_INFO_TYPE`\
Initialiser/utiliser le `bstrType` champ.

`DEBUGPROP_INFO_VALUE`\
Initialiser/utiliser le `bstrValue` champ.

`DEBUGPROP_INFO_ATTRIB`\
Initialiser/utiliser le `dwAttrib` champ.

`DEBUGPROP_INFO_PROP`\
Initialize/utilise le `pProperty` champ qui contient une interface [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) .

`DEBUGPROP_INFO_VALUE_AUTOEXPAND`\
Spécifie que le champ de valeur doit contenir la valeur développée automatiquement, si elle est disponible, pour ce type d’objet.

`DEBUGPROP_INFO_VALUE_NOFUNCEVAL`\
Action déconseillée.

`DEBUGPROP_INFO_VALUE_RAW`\
Ne retournez pas de valeurs ou de membres embellis (autrement dit, ne mettez pas en forme les valeurs).

`DEBUGPROP_INFO_VALUE_NO_TOSTRING`\
Ne retournez pas de valeurs synthétisées spéciales (par exemple, n’appelez pas `ToString()` sur un objet pour produire une valeur).

`DEBUGPROP_INFO_NONE`\
Spécifie qu'aucun indicateur n'est défini.

`DEBUGPROP_INFO_STANDARD`\
Initialisez/utilisez les `dwAttrib` champs,, `bstrName` `bstrType` et `bstrValue` .

`DEBUGPROP_INFO_All`\
Indique un masque de tous les indicateurs.

## <a name="remarks"></a>Notes
Ces valeurs sont passées aux méthodes [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)et [EnumProperties,](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) pour indiquer les champs à initialiser à la structure [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) .

Ces valeurs sont également utilisées pour le `dwFields` membre de la `DEBUG_PROPERTY_INFO` structure pour indiquer les champs de la structure qui sont utilisés et valides lorsque la structure est retournée.

Ces valeurs peuvent être combinées avec une opération de bits `OR` .

## <a name="requirements"></a>Configuration requise
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
