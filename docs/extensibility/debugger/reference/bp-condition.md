---
title: BP_CONDITION Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 88ed6b6468c5765c8f987c1f15f3e4e8ade9c8c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738106"
---
# <a name="bp_condition"></a>BP_CONDITION
Décrit les conditions dans lesquelles un point de rupture s’allume.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _BP_CONDITION {
    IDebugThread2* pThread;
    BP_COND_STYLE  styleCondition;
    BSTR           bstrContext;
    BSTR           bstrCondition;
    UINT           nRadix;
} BP_CONDITION;
```

```csharp
public struct BP_CONDITION {
    public IDebugThread2 pThread;
    public uint          styleCondition;
    public string        bstrContext;
    public string        bstrCondition;
    public uint          nRadix;
};
```

## <a name="members"></a>Membres
`pThread`\
[L’objet IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) qui représente le fil actif pour l’application qui contient le point d’arrêt.

`styleCondition`\
Une valeur de [l’énumération BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) décrivant le style de cette condition de point de rupture.

`bstrContext`\
L’emplacement du point d’arrêt.

`bstrCondition`\
L’état de tir du point d’arrêt.

`nRadix`\
Radix à utiliser dans l’évaluation de toute information numérique.

## <a name="remarks"></a>Notes
Cette structure est membre des structures [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) et [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

Cette structure est également transmise comme paramètre aux méthodes [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) et [SetCondition.](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)
