---
title: UNMANAGED_ADDRESS_THIS_RELATIVE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE
helpviewer_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE structure
ms.assetid: e6a91ace-2d47-4ff9-aefb-8d8b68eab0b2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5c19109215a9e8824f1648860c39ccb33836ca93
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879993"
---
# <a name="unmanaged_address_this_relative"></a>UNMANAGED_ADDRESS_THIS_RELATIVE
Cette structure représente une adresse relative à un `this` pointeur ( `Me` en Visual Basic).

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _tagUNMANAGED_THIS_RELATIVE {
   DWORD dwOffset;
   DWORD dwBitOffset;
   DWORD dwBitLength;
} UNMANAGED_ADDRESS_THIS_RELATIVE;
```

```csharp
public struct UNMANAGED_THIS_RELATIVE {
   public uint dwOffset;
   public uint dwBitOffset;
   public uint dwBitLength;
}
```

## <a name="members"></a>Membres
 `dwOffset`\
 Décalage d’octet d’une position de base (par exemple, début d’une classe vtable).

 `dwBitOffset`\
 Décalage en bits à partir d’une position de base (toujours 0, sauf en faisant référence à un champ de bits).

 `dwBitLength`\
 Nombre de bits représentant l’adresse (toujours 0, sauf si vous faites référence à un champ de bits).

## <a name="remarks"></a>Remarques
 Cette structure fait partie de l’Union de la structure [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) lorsque le `dwKind` champ de la `DEBUG_ADDRESS_UNION` structure a la valeur `ADDRESS_KIND_UNMANAGED_THIS_RELATIVE` (une valeur de l’énumération [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) ).

## <a name="requirements"></a>Configuration requise
 En-tête : SH. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
