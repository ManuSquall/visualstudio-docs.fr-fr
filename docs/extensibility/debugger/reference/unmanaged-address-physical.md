---
title: UNMANAGED_ADDRESS_PHYSICAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_PHYSICAL
helpviewer_keywords:
- UNMANAGED_ADDRESS_PHYSICAL structure
ms.assetid: fed09686-caa6-4efc-851e-a0432019e9d0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93f6d1094a490041cd04a47fa073d2e75b8d2e23
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316120"
---
# <a name="unmanagedaddressphysical"></a>UNMANAGED_ADDRESS_PHYSICAL
Cette structure représente une adresse physique.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _tagUNMANAGED_ADDRESS_PHYSICAL {
   ULONGLONG offset;
} UNMANAGED_ADDRESS_PHYSICAL;
```

```csharp
public struct UNMANAGED_ADDRESS_PHYSICAL {
   public ulong offset;
}
```

## <a name="members"></a>Membres
 `offset`\
 Un décalage 64 bits dans un espace d’adressage physique.

## <a name="remarks"></a>Notes
 Cette structure fait partie de l’union dans le [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) structure lorsque le `dwKind` champ la `DEBUG_ADDRESS_UNION` structure est définie sur `ADDRESS_KIND_UNMANAGED_PHYSICAL` (une valeur comprise entre le [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) énumération).

## <a name="requirements"></a>Configuration requise
 En-tête : sh.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)