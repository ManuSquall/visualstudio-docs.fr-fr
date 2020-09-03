---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 162a64c9118bdcde23208082350005e607a237b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736604"
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
