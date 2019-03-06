---
title: UNMANAGED_ADDRESS_THIS_RELATIVE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE
helpviewer_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE structure
ms.assetid: e6a91ace-2d47-4ff9-aefb-8d8b68eab0b2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e9d2bf87a804295a5ea8f6750ee9cd93643c53bc
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719650"
---
# <a name="unmanagedaddressthisrelative"></a>UNMANAGED_ADDRESS_THIS_RELATIVE
Cette structure représente une adresse qui est relative à un `this` pointeur (`Me` en Visual Basic).

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

## <a name="terms"></a>Termes
 dwOffset décalage d’octet d’une position de base (par exemple, le début d’un vtable de la classe).

 dwBitOffset décalage de bits à partir d’une position de base (toujours 0, sauf si la référence à un champ de bits).

 Nombre de bits qui représente l’adresse de dwBitLength (toujours 0, sauf si la référence à un champ de bits).

## <a name="remarks"></a>Notes
 Cette structure fait partie de l’union dans le [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) structure lorsque le `dwKind` champ la `DEBUG_ADDRESS_UNION` structure est définie sur `ADDRESS_KIND_UNMANAGED_THIS_RELATIVE` (une valeur comprise entre le [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) énumération).

## <a name="requirements"></a>Spécifications
 En-tête : sh.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)