---
title: METADATA_ADDRESS_LOCAL Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3adf9ca5f679c7a526f10b1ee6c91d50dac52d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714474"
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
L’ID de la méthode ou de la fonction de la variable locale fait partie de.

[C] `_mdToken` est `typedef` un pour un 32 bits `int`.

`pLocal`\
Le jeton dont cette structure représente l’adresse.

`dwIndex`\
Peut être l’index de cette variable locale dans la méthode ou la fonction, ou une autre valeur (spécifique à la langue).

## <a name="remarks"></a>Notes

Cette structure fait partie du [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) syndicat dans la `dwKind` structure DEBUG_ADDRESS_UNION `DEBUG_ADDRESS_UNION` lorsque le `ADDRESS_KIND_LOCAL` champ de la structure est fixé à (une valeur de [l’ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) énumération).

> [!WARNING]
> [C seulement] Si `pLocal` elle n’est pas `Release` nulle, alors`addr` vous devez faire appel au pointeur symbolique (est un champ dans la structure [DEBUG_ADDRESS)](../../../extensibility/debugger/reference/debug-address.md) :
>
> ```cpp
> if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
> {
>     addr.addr.addrLocal.pLocal->Release();
> }
> ```

## <a name="requirements"></a>Spécifications

En-tête: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi

- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
