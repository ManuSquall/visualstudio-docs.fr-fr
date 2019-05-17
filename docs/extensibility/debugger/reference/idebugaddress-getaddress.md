---
title: IDebugAddress::GetAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3b2829e598a9dff08218d5fc19c34089d07b2601
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615318"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Retourne une structure qui décrit un objet et son emplacement dans son étendue ou le conteneur.

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
[in, out] Un [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) structure est remplie par cette méthode.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Le [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) structure est passée à cette méthode, qui ensuite le remplit avec les informations appropriées. Interprétation de ces informations varie selon le type d’informations renvoyées et le Gestionnaire de symbole lui-même. Consultez [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) pour plus d’informations.

## <a name="see-also"></a>Voir aussi
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)