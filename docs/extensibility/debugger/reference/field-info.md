---
title: FIELD_INFO Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e2089746adecc583d04176afca18ad19826ea53
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736897"
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
Une combinaison de drapeaux de [l’FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) énumération qui précise quels membres sont remplis.

`bstrFullName`\
Le nom complet du champ.

`bstrName`\
Le nom court du champ.

`bstrType`\
Type du champ.

`dwModifiers`\
Une combinaison de drapeaux de [l’FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) énumération qui décrit le champ.

## <a name="remarks"></a>Notes
Cette structure est transmise à la méthode [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) où elle est remplie.

## <a name="requirements"></a>Spécifications
En-tête: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
