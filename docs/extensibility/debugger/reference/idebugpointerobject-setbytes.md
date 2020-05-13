---
title: IDebugPointerObject::SetBytes ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dede3ee5291afbfbeab4d6e60dcbd56e205e4526
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725501"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
Définit la valeur indiquée à partir d’une série d’octets consécutifs.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int SetBytes(
   uint     dwStart,
   uint     dwCount,
   byte[]   pBytes,
   out uint pdwBytes
);
```

## <a name="parameters"></a>Paramètres
`dwStart`\
[dans] Un décalage, dans les octets, dès le début de l’objet pointé vers.

`dwCount`\
[dans] Le nombre d’octets à définir.

`pBytes`\
[dans] Une gamme d’octets représentant la nouvelle valeur. Cette valeur est stockée dans l’objet, à partir du décalage donné.

`pdwBytes`\
[out] Retourne le nombre d’octets effectivement définis.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK; autrement, renvoie un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode est utilisée si le pointeur représenté par cet [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) pointe vers un type primitif ou un simple tableau de types primitifs (c’est-à-dire un tableau qui peut être représenté par une simple séquence d’octets). Cet `IDebugPointerObject` objet ne peut pas être une référence nulle (il doit indiquer une adresse dans la mémoire).

## <a name="see-also"></a>Voir aussi
- [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
