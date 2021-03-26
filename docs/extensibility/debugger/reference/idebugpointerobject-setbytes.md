---
description: Définit la valeur vers laquelle pointe une série d’octets consécutifs.
title: 'IDebugPointerObject :: SetBytes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 015a7782fae01f06a9d1cc4a5e64090303d2f2e0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087585"
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
