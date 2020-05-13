---
title: DEBUG_ADDRESS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe778ba3ed80930a4cd7b4fa1170f286b3ccf6ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737510"
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
Le GUID du module qui contient cette adresse.

`tokClass`\
Le jeton identifiant la classe ou le type de cette adresse.

> [!NOTE]
> Cette valeur est spécifique à un fournisseur de symboles et n’a donc pas de signification générale autre que comme un identifiant pour un type de classe.

`addr`\
Une structure [DEBUG_ADDRESS_UNION,](../../../extensibility/debugger/reference/debug-address-union.md) qui contient une union de structures qui décrivent les types d’adresses individuelles. La `addr`valeur .`dwKind` vient de [l’énumération ADDRESS_KIND,](../../../extensibility/debugger/reference/address-kind.md) ce qui explique comment interpréter le syndicat.

## <a name="remarks"></a>Notes
Cette structure est transmise à la méthode [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) à remplir.

**Avertissement [C seulement]**

Si `addr.dwKind` `ADDRESS_KIND_METADATA_LOCAL` est `addr.addr.addrLocal.pLocal` et si n’est pas `Release` une valeur nulle, alors vous devez faire appel sur le pointeur symbolique:

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>Spécifications
En-tête: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
