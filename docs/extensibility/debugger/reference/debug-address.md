---
description: Cette structure représente une adresse.
title: DEBUG_ADDRESS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1b250654f45f18adcfd9c52a6047b2b8798be75b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096367"
---
# <a name="debug_address"></a>DEBUG_ADDRESS
Cette structure représente une adresse.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _tagDEBUG_ADDRESS {
    ULONG32             ulAppDomainID;
    GUID                guidModule;
    _mdToken            tokClass;
    DEBUG_ADDRESS_UNION addr;
} DEBUG_ADDRESS;
```

```csharp
public struct DEBUG_ADDRESS {
    public uint                ulAppDomainID;
    public Guid                guidModule;
    public int                 tokClass;
    public DEBUG_ADDRESS_UNION addr;
}
```

## <a name="members"></a>Membres
`ulAppDomainID`\
ID de processus.

`guidModule`\
GUID du module qui contient cette adresse.

`tokClass`\
Jeton identifiant la classe ou le type de cette adresse.

> [!NOTE]
> Cette valeur est spécifique à un fournisseur de symboles et n’a par conséquent aucune signification générale autre que l’identificateur d’un type de classe.

`addr`\
Structure [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) , qui contient une Union de structures qui décrivent les types d’adresses individuels. Valeur `addr` .`dwKind` provient de l’énumération [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) , qui explique comment interpréter l’Union.

## <a name="remarks"></a>Notes
Cette structure est passée à la méthode [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) à remplir.

**Avertissement (C++ uniquement)**

Si `addr.dwKind` a `ADDRESS_KIND_METADATA_LOCAL` `addr.addr.addrLocal.pLocal` la valeur et si n’est pas une valeur null, vous devez appeler `Release` sur le pointeur de jeton :

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>Spécifications
En-tête : SH. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
