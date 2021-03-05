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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 52c52d12d8c357f4dbadeef673a3dc4474713ce9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145441"
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
