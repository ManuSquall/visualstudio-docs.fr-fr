---
title: DEBUG_ADDRESS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc25fb53db918486029e931a06a9e2de37f81c5a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346305"
---
# <a name="debugaddress"></a>DEBUG_ADDRESS
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
L’ID de processus.

`guidModule`\
Le GUID du module qui contient cette adresse.

`tokClass`\
Le jeton identifiant la classe ou un type de cette adresse.

> [!NOTE]
> Cette valeur est spécifique à un fournisseur de symboles et ne possède donc aucun sens général différent en tant qu’identificateur pour un type de classe.

`addr`\
Un [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) structure qui contient une union de structures qui décrivent les types d’adresses individuelles. La valeur `addr`.`dwKind` provient de la [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) énumération, qui explique comment interpréter l’union.

## <a name="remarks"></a>Notes
Cette structure est passée à la [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) méthode doit être renseigné.

**Avertissement [C++ uniquement]**

Si `addr.dwKind` est `ADDRESS_KIND_METADATA_LOCAL` et si `addr.addr.addrLocal.pLocal` n’est pas une valeur null, vous devez l’appeler `Release` sur le pointeur de jeton :

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>Configuration requise
En-tête : sh.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
