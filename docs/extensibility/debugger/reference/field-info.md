---
description: Cette structure décrit une variable locale, un paramètre ou un autre champ.
title: FIELD_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27055178f01f41bb6b4642b8c4d70ea6346b9e74
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059417"
---
# <a name="field_info"></a>FIELD_INFO
Cette structure décrit une variable locale, un paramètre ou un autre champ.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _tagFieldInfo {
    FIELD_INFO_FIELDS dwFields;
    BSTR              bstrFullName;
    BSTR              bstrName;
    BSTR              bstrType;
    FIELD_MODIFIERS   dwModifiers;
} FIELD_INFO;
```

```csharp
public struct FIELD_INFO {
    public uint   dwFields;
    public string bstrFullName;
    public string bstrName;
    public string bstrType;
    public uint   dwModifiers;
};
```

## <a name="members"></a>Membres
`dwFields`\
Combinaison d’indicateurs de l’énumération [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) qui spécifie les membres qui sont remplis.

`bstrFullName`\
Nom complet du champ.

`bstrName`\
Nom abrégé du champ.

`bstrType`\
Type du champ.

`dwModifiers`\
Combinaison d’indicateurs de l’énumération [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) qui décrit le champ.

## <a name="remarks"></a>Notes
Cette structure est transmise à la méthode [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) où elle est remplie.

## <a name="requirements"></a>Spécifications
En-tête : SH. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
