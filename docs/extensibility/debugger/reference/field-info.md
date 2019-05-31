---
title: FIELD_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 352e4bdf6c79dc67f0bf396cb1164e96e80fbf5f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337702"
---
# <a name="fieldinfo"></a>FIELD_INFO
Une variable locale, paramètre ou autre champ décrite par cette structure.

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
Une combinaison d’indicateurs de la [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) énumération qui indique quels membres sont renseignés.

`bstrFullName`\
Le nom complet du champ.

`bstrName`\
Le nom court du champ.

`bstrType`\
Le type du champ.

`dwModifiers`\
Une combinaison d’indicateurs de la [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) énumération qui décrit le champ.

## <a name="remarks"></a>Notes
Cette structure est passée à la [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) méthode où il est renseigné.

## <a name="requirements"></a>Configuration requise
En-tête : sh.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
