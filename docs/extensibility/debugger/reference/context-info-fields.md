---
description: Spécifie les informations à récupérer sur un contexte de mémoire.
title: CONTEXT_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 878dfb4e2f684b7a28b06820e110b22cdae962b9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096445"
---
# <a name="context_info_fields"></a>CONTEXT_INFO_FIELDS
Spécifie les informations à récupérer sur un contexte de mémoire.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_CONTEXT_INFO_FIELDS {
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
Initialisez/utilisez le `bstrModuleUrl` champ de la structure [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) .

`CIF_FUNCTION`\
Initialisez/utilisez le `bstrFunction` champ de la `CONTEXT_INFO` structure.

`CIF_FUNCTIONOFFSET`\
Initialisez/utilisez le `posFunctionOffset` champ de la `CONTEXT_INFO` structure.

`CIF_ADDRESS`\
Initialisez/utilisez le `bstrAddress` champ de la `CONTEXT_INFO` structure.

`CIF_ADDRESSOFFSET`\
Initialisez/utilisez le `bstrAddressOffset` champ de la `CONTEXT_INFO` structure.

`CIF_ALLFIELDS`\
Initialisez/Utilisez tous les champs de la `CONTEXT_INFO` structure.

## <a name="remarks"></a>Notes
Un paramètre est passé à la méthode [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) pour indiquer les champs de la structure [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) qui doivent être initialisés.

Ces indicateurs sont également utilisés pour indiquer les champs de la `CONTEXT_INFO` structure qui sont utilisés et valides lorsque la structure est retournée.

Ces valeurs peuvent être combinées avec une opération or au niveau du bit.

## <a name="requirements"></a>Spécifications
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
