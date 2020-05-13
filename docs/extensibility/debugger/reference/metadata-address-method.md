---
title: METADATA_ADDRESS_METHOD Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_METHOD
helpviewer_keywords:
- METADATA_ADDRESS_METHOD structure
ms.assetid: fc0e5370-1b4f-4867-837f-0d63c4b9dd09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc3dd7a34e4f9a3e1b933781aeaf4e18cad7ec17
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714456"
---
# <a name="metadata_address_method"></a>METADATA_ADDRESS_METHOD
Cette structure représente l’adresse d’une méthode d’une classe.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _tagMETADATA_ADDRESS_METHOD {
   _mdToken tokMethod;
   DWORD    dwOffset;
   DWORD    dwVersion;
} METADATA_ADDRESS_METHOD;
```

```csharp
public struct METADATA_ADDRESS_METHOD {
   public int  tokMethod;
   public uint dwOffset;
   public uint dwVersion;
}
```

## <a name="members"></a>Membres
 `tokMethod`\
 L’ID de la méthode.

 [C] `_mdToken` est `typedef` un pour un 32 bits `int`.

 `dwOffset`\
 Le décalage du début de classe à cette méthode (peut représenter le décalage dans le vtable).

 `dwVersion`\
 La version de la méthode (cette valeur est unique au fournisseur de symboles).

## <a name="remarks"></a>Notes
 Cette structure fait partie du [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) syndicat dans la `dwKind` structure DEBUG_ADDRESS_UNION `DEBUG_ADDRESS_UNION` lorsque le `ADDRESS_KIND_METHOD` champ de la structure est fixé à (une valeur de [l’ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) énumération).

## <a name="requirements"></a>Spécifications
 En-tête: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
