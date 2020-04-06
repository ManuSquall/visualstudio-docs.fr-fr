---
title: IDebugBoundBreakpoint2::GetHitCount (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::GetHitCount
helpviewer_keywords:
- GetHitCount method
- IDebugBoundBreakpoint2::GetHitCount method
ms.assetid: 23481f37-047c-41d2-8286-4da1f4084961
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c821470cc81c1f4c495f6d71565d79cc9745f65d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735518"
---
# <a name="idebugboundbreakpoint2gethitcount"></a>IDebugBoundBreakpoint2::GetHitCount
Obtient le nombre de coups en cours pour ce point d’arrêt lié.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetHitCount( 
   DWORD* pdwHitCount
);
```

```csharp
int GetHitCount( 
   out uint pdwHitCount
);
```

## <a name="parameters"></a>Paramètres
`pdwHitCount`\
[out] Retourne le nombre de coups.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Retourne `E_BP_DELETED` si l’état de l’objet `BPS_DELETED` de rupture lié est réglé (une partie du [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) énumération).

## <a name="remarks"></a>Notes
 Le nombre de coups est le nombre de fois que ce point d’arrêt a tiré pendant la course actuelle de la session.

## <a name="see-also"></a>Voir aussi
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
