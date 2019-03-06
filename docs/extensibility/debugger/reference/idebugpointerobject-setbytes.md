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
ms.openlocfilehash: e54a7f38eed85ffe2757b373de1af59e1aaa126b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694724"
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

#### <a name="parameters"></a>Paramètres
 `dwStart`

 [in] Offset, en octets, à partir du début de l’objet désigné.

 `dwCount`

 [in] Le nombre d’octets à définir.

 `pBytes`

 [in] Un tableau d’octets représentant la nouvelle valeur. Cette valeur est stockée dans l’objet, en commençant à l’offset donné.

 `pdwBytes`

 [out] Retourne que le nombre d’octets réellement définie.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode est utilisée si le pointeur comme représenté par ce [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) pointe vers un type primitif ou un simple tableau de types primitifs (autrement dit, un tableau qui peut être représenté par une simple séquence d’octets). Cela `IDebugPointerObject` objet ne peut pas être une référence null (il doit pointer vers une adresse en mémoire).

## <a name="see-also"></a>Voir aussi
- [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)