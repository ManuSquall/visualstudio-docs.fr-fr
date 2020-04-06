---
title: METADATA_ADDRESS_PARAM Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_PARAM
helpviewer_keywords:
- METADATA_ADDRESS_PARAM structure
ms.assetid: 90904f19-0e71-4cb3-a56e-6a2e92f66dfc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a0319cfc6f2be817a25126e67cdc470bc727a4ca
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714440"
---
# <a name="metadata_address_param"></a>METADATA_ADDRESS_PARAM
Cette structure représente un paramètre d’une méthode ou d’une fonction.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _tagMETADATA_ADDRESS_PARAM {
   _mdToken tokMethod;
   _mdToken tokParam;
   DWORD    dwIndex;
} METADATA_ADDRESS_PARAM;
```

```csharp
public struct METADATA_ADDRESS_PARAM {
   public int  tokMethod;
   public int  tokParam;
   public uint dwIndex;
}
```

## <a name="members"></a>Membres
 `tokMethod`\
 L’ID de la méthode dont fait partie le paramètre.

 `tokParam`\
 ID du paramètre.

 `dwIndex`\
 L’index du paramètre dans une liste de paramètres.

## <a name="remarks"></a>Notes
 Cette structure fait partie du [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) syndicat dans la `dwKind` structure DEBUG_ADDRESS_UNION `DEBUG_ADDRESS_UNION` lorsque le `ADDRESS_KIND_PARAM` champ de la structure est fixé à (une valeur de [l’ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) énumération).

## <a name="requirements"></a>Spécifications
 En-tête: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
