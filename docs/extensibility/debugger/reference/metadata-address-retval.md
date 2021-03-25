---
description: Cette structure représente une valeur de retour d’une méthode ou d’une fonction.
title: METADATA_ADDRESS_RETVAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_RETVAL
helpviewer_keywords:
- METADATA_ADDRESS_RETVAL structure
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5e28e0c32d5039ba0deda9a8c6801e6969c4ad96
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079881"
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
 ID de la méthode pour laquelle cette valeur de retour est.

 `dwCorType`\
 Type de base de la valeur de retour. Il s’agit d’une valeur de l' `CorElementType` énumération définie dans le fichier .NET Framework SDK corhdr. h.

 `dwSigSize`\
 Taille de la signature de la valeur de retour (telle qu’elle est stockée dans `rgSig` ).

 `rgSig`\
 Tableau d’octets formant la signature de la valeur de retour.

## <a name="remarks"></a>Notes
 Cette structure fait partie de l’Union de la structure [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) lorsque le `dwKind` champ de la `DEBUG_ADDRESS_UNION` structure a la valeur `ADDRESS_KIND_RETVAL` (une valeur de l’énumération [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) ).

## <a name="requirements"></a>Spécifications
 En-tête : SH. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
