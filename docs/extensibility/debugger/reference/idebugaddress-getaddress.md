---
title: IDebugAddress::GetAddress ( Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736604"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Renvoie une structure décrivant un objet et son emplacement dans son champ d’application ou son conteneur.

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
[dans, dehors] Une structure [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) qui est remplie par cette méthode.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK; autrement, renvoie un code d’erreur.

## <a name="remarks"></a>Notes
 La [structure DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) est transmise à cette méthode, qui la remplit ensuite avec les informations appropriées. La façon dont cette information est interprétée dépend du type d’information retournée et du gestionnaire de symbole lui-même. Voir [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) pour plus de détails.

## <a name="see-also"></a>Voir aussi
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
