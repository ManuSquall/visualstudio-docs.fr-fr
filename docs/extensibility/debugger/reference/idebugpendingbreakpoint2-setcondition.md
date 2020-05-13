---
title: IDebugPendingBreakpoint2::SetCondition (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugPendingBreakpoint2::SetCondition method
ms.assetid: 0534224f-654f-4862-bc4d-a9a81a5f8899
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4683d944f2489b8b21ff545c86e3d867283d644a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725726"
---
# <a name="idebugpendingbreakpoint2setcondition"></a>IDebugPendingBreakpoint2::SetCondition
Définit ou modifie la condition associée au point d’arrêt en attente.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetCondition( 
   BP_CONDITION bpCondition
);
```

```csharp
int SetCondition( 
   BP_CONDITION bpCondition
);
```

## <a name="parameters"></a>Paramètres
`bpCondition`\
[dans] Une structure [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) qui spécifie la condition à régler.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Toute condition qui était auparavant associée au point d’arrêt en attente est perdue. Tous les points de rupture liés à partir de ce point d’arrêt en attente sont appelés à définir leur état à la valeur spécifiée dans le `bpCondition` paramètre.

## <a name="see-also"></a>Voir aussi
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
