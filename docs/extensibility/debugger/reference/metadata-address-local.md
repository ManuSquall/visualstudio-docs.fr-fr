---
description: Cette structure représente l’adresse d’une variable locale dans une portée (généralement une fonction ou une méthode).
title: METADATA_ADDRESS_LOCAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c265f8312b9a23b3b10f06595240dae20894f001
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061548"
---
# <a name="metadata_address_local"></a>METADATA_ADDRESS_LOCAL

Cette structure représente l’adresse d’une variable locale dans une portée (généralement une fonction ou une méthode).

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _tagMETADATA_ADDRESS_LOCAL {
    _mdToken  tokMethod;
    IUnknown* pLocal;
    DWORD     dwIndex;
} METADATA_ADDRESS_LOCAL;
```

```csharp
public struct METADATA_ADDRESS_LOCAL {
    public int    tokMethod;
    public object pLocal;
    public uint   dwIndex;
}
```

## <a name="members"></a>Membres

`tokMethod`\
ID de la méthode ou de la fonction dont fait partie la variable locale.

(C++) `_mdToken` est un `typedef` pour un 32 bits `int` .

`pLocal`\
Jeton dont l’adresse est représentée par cette structure.

`dwIndex`\
Peut être l’index de cette variable locale dans la méthode ou la fonction, ou une autre valeur (propre à la langue).

## <a name="remarks"></a>Notes

Cette structure fait partie de l’Union de la structure [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) lorsque le `dwKind` champ de la `DEBUG_ADDRESS_UNION` structure a la valeur `ADDRESS_KIND_LOCAL` (une valeur de l’énumération [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) ).

> [!WARNING]
> [C++ uniquement] Si `pLocal` n’a pas la valeur null, vous devez appeler `Release` sur le pointeur de jeton ( `addr` est un champ de la structure [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) ) :
>
> ```cpp
> if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
> {
>     addr.addr.addrLocal.pLocal->Release();
> }
> ```

## <a name="requirements"></a>Spécifications

En-tête : SH. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi

- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
