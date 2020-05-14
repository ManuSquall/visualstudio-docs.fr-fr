---
title: METADATA_ADDRESS_RETVAL Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_RETVAL
helpviewer_keywords:
- METADATA_ADDRESS_RETVAL structure
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f2437d10078eb623e063b3292d96ef9bb4a9cf64
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714275"
---
# <a name="metadata_address_retval"></a>METADATA_ADDRESS_RETVAL
Cette structure représente une valeur de retour d’une méthode ou d’une fonction.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _tagMETADATA_ADDRESS_RETVAL {
   _mdToken tokMethod;
   DWORD    dwCorType;
   DWORD    dwSigSize;
   BYTE     rgSig[10];
} METADATA_ADDRESS_RETVAL;
```

```csharp
public struct METADATA_ADDRESS_RETVAL {
   public int    tokMethod;
   public uint   dwCorType;
   public uint   dwSigSize;
   public byte[] rgSig;
}
```

## <a name="members"></a>Membres
 `tokMethod`\
 L’ID de la méthode de cette valeur de retour est pour.

 `dwCorType`\
 Le type de base de valeur de retour. Il s’agit `CorElementType` d’une valeur de l’énumération définie dans le fichier .NET Framework SDK corhdr.h.

 `dwSigSize`\
 La taille de la signature de `rgSig`valeur de retour (comme stocké dans ).

 `rgSig`\
 Une gamme d’octets formant la signature de la valeur de retour.

## <a name="remarks"></a>Notes
 Cette structure fait partie du [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) syndicat dans la `dwKind` structure DEBUG_ADDRESS_UNION `DEBUG_ADDRESS_UNION` lorsque le `ADDRESS_KIND_RETVAL` champ de la structure est fixé à (une valeur de [l’ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) énumération).

## <a name="requirements"></a>Spécifications
 En-tête: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
