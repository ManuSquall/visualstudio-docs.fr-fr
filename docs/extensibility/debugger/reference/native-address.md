---
title: NATIVE_ADDRESS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- NATIVE_ADDRESS
helpviewer_keywords:
- NATIVE_ADDRESS structure
ms.assetid: 7a0cd085-bfc8-45cc-a3d4-4459070e207a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d7d061d7cd60444a523d5764c30b7ff538faefe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913767"
---
# <a name="nativeaddress"></a>NATIVE_ADDRESS

Cette structure représente une adresse native.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _tagNATIVE_ADDRESS {
    DWORD unknown;
} NATIVE_ADDRESS;
```

```csharp
public struct NATIVE_ADDRESS {
    public uint unknown;
}
```

## <a name="terms"></a>Termes

`unknown`

L’adresse native (la signification de ce dépend de l’exécution et le système d’exploitation).

## <a name="remarks"></a>Notes

Cette structure fait partie de l’union dans le [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) structure lorsque le `dwKind` champ la `DEBUG_ADDRESS_UNION` structure est définie sur `ADDRESS_KIND_NATIVE` (une valeur comprise entre le [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) énumération).

## <a name="requirements"></a>Configuration requise

En-tête : sh.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi

- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
