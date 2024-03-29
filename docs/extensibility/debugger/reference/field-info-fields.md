---
description: Spécifie les informations à récupérer sur un objet IDebugField.
title: FIELD_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0bd13473be5817e821f61b646bd1634cfe06388b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059425"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
Spécifie les informations à récupérer sur un objet [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_FIELD_INFO_FIELDS { 
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
Initialisez/utilisez le `bstrFullName` champ de la structure [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) .

`FIF_NAME`\
Initialisez/utilisez le `bstrName` champ de la `FIELD_INFO` structure.

`FIF_TYPE`\
Initialisez/utilisez le `bstrType` champ de la `FIELD_INFO` structure.

`FIF_MODIFIERS`\
Initialisez/utilisez le `bstrModifiers` champ de la `FIELD_INFO` structure.

## <a name="remarks"></a>Notes
Ces valeurs sont également passées comme argument à la méthode [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) pour spécifier les champs de la structure [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) qui doivent être initialisés.

Ces valeurs sont également utilisées dans le `dwFields` membre de la `FIELD_INFO` structure pour indiquer les champs qui sont utilisés et valides.

Ces indicateurs peuvent être combinés avec une opération au niveau du bit `OR` .

## <a name="requirements"></a>Spécifications
En-tête : SH. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
