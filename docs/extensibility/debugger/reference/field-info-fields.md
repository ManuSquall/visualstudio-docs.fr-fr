---
title: FIELD_INFO_FIELDS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9a3d2e796d37606c51918d8e49db920161d63f55
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736908"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
Précise les informations à récupérer sur un objet [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_FIELD_INFO_FIELDS { 
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
typedef DWORD FIELD_INFO_FIELDS;
```

```csharp
public enum enum_FIELD_INFO_FIELDS {
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
```

## <a name="fields"></a>Champs
`FIF_FULLNAME`\
Initialiser/utiliser `bstrFullName` le champ dans la structure [FIELD_INFO.](../../../extensibility/debugger/reference/field-info.md)

`FIF_NAME`\
Initialiser/utiliser `bstrName` le champ `FIELD_INFO` dans la structure.

`FIF_TYPE`\
Initialiser/utiliser `bstrType` le champ `FIELD_INFO` dans la structure.

`FIF_MODIFIERS`\
Initialiser/utiliser `bstrModifiers` le champ `FIELD_INFO` dans la structure.

## <a name="remarks"></a>Notes
Ces valeurs sont également transmises comme un argument à la méthode [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) pour préciser quels domaines de la structure [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) doivent être parasécisés.

Ces valeurs sont également `dwFields` utilisées `FIELD_INFO` dans le membre de la structure pour indiquer quels champs sont utilisés et valides.

Ces drapeaux peuvent être combinés avec un peu plus. `OR`

## <a name="requirements"></a>Spécifications
En-tête: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
