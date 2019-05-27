---
title: IDebugPointerObject::SetBytes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b574e28ac0b42f065bfbf056188c655797e542b
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66209344"
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
[in] Offset, en octets, à partir du début de l’objet désigné.

`dwCount`\
[in] Le nombre d’octets à définir.

`pBytes`\
[in] Un tableau d’octets représentant la nouvelle valeur. Cette valeur est stockée dans l’objet, en commençant à l’offset donné.

`pdwBytes`\
[out] Retourne que le nombre d’octets réellement définie.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode est utilisée si le pointeur comme représenté par ce [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) pointe vers un type primitif ou un simple tableau de types primitifs (autrement dit, un tableau qui peut être représenté par une simple séquence d’octets). Cela `IDebugPointerObject` objet ne peut pas être une référence null (il doit pointer vers une adresse en mémoire).

## <a name="see-also"></a>Voir aussi
- [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)