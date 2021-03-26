---
description: Obtient la valeur pointée sous la forme d’une série d’octets consécutifs.
title: 'IDebugPointerObject :: GetBytes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a150f819610de97ee292302d89e2007c6235aae
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087624"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
Obtient la valeur pointée sous la forme d’une série d’octets consécutifs.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int GetBytes(
   uint       dwStart,
   uint       dwCount,
   out byte[] pBytes,
   out uint   pdwBytes
);
```

## <a name="parameters"></a>Paramètres
`dwStart`\
dans Offset, en octets, à partir du début de l’objet vers lequel pointe.

`dwCount`\
dans Nombre d’octets à récupérer.

`pBytes`\
[in, out] Tableau qui est rempli avec la valeur sous la forme d’une série d’octets consécutifs, en commençant au décalage donné par rapport à l’objet pointé.

`pdwBytes`\
à Retourne le nombre d’octets réellement récupérés.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode est utilisée si le pointeur représenté par ce [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) pointe vers un type primitif ou un tableau simple de types primitifs (autrement dit, un tableau qui peut être représenté par une séquence simple d’octets).

## <a name="see-also"></a>Voir aussi
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
