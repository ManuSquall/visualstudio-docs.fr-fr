---
title: IDebugBoundBreakpoint2::SetPassCount (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugBoundBreakpoint2::SetPassCount method
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bcc7bd57ce0c392a2874f107c6e4d8d5753399d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735436"
---
# <a name="idebugboundbreakpoint2setpasscount"></a>IDebugBoundBreakpoint2::SetPassCount
Définit ou modifie le nombre de laissez-passer associé à ce point de rupture lié.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

```csharp
int SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

## <a name="parameters"></a>Paramètres
`bpPassCount`\
[dans] La [structure BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) qui spécifie le nombre de laissez-passer.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Retourne `E_BP_DELETED` si l’état de l’objet `BPS_DELETED` de rupture lié est réglé (une partie du [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) énumération).

## <a name="remarks"></a>Notes
 Le nombre de laissez-passer détermine quand le point d’arrêt est tiré. Le nombre de laissez-passer ou de frappe actuel peut être obtenu en appelant la méthode [GetHitCount.](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)

 Tout nombre de passes qui était auparavant associé à ce point d’arrêt est perdu.

## <a name="see-also"></a>Voir aussi
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
