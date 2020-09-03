---
title: 'IDebugPointerObject :: SetBytes | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725501"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
Définit la valeur vers laquelle pointe une série d’octets consécutifs.

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
dans Offset, en octets, à partir du début de l’objet vers lequel pointe.

`dwCount`\
dans Nombre d’octets à définir.

`pBytes`\
dans Tableau d’octets représentant la nouvelle valeur. Cette valeur est stockée dans l’objet, en commençant à l’offset donné.

`pdwBytes`\
à Retourne le nombre d’octets réellement définis.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode est utilisée si le pointeur représenté par ce [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) pointe vers un type primitif ou un tableau simple de types primitifs (autrement dit, un tableau qui peut être représenté par une séquence simple d’octets). Cet `IDebugPointerObject` objet ne peut pas être une référence null (il doit pointer vers une adresse en mémoire).

## <a name="see-also"></a>Voir aussi
- [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
