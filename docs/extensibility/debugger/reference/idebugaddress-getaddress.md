---
description: Retourne une structure décrivant un objet et son emplacement dans son étendue ou conteneur.
title: 'IDebugAddress :: GetAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 92e616ded029c22b16b81ccd5f25086b11be6ff4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094395"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Retourne une structure décrivant un objet et son emplacement dans son étendue ou conteneur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetAddress (
   DEBUG_ADDRESS * pAddress
);
```

```csharp
int GetAddress(
   DEBUG_ADDRESS[] pAddress
);
```

## <a name="parameters"></a>Paramètres
`pAddress`\
[in, out] Structure [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) qui est remplie par cette méthode.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 La structure [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) est passée à cette méthode, qui la remplit avec les informations appropriées. La façon dont ces informations sont interprétées dépend du type d’informations retourné et du gestionnaire de symboles lui-même. Pour plus d’informations, consultez [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) .

## <a name="see-also"></a>Voir aussi
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
