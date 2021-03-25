---
description: Décrit les conditions dans lesquelles un point d’arrêt est déclenché.
title: BP_CONDITION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 560cf7184e5fa7b25e35410313535675713742aa
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085336"
---
# <a name="bp_condition"></a>BP_CONDITION
Décrit les conditions dans lesquelles un point d’arrêt est déclenché.

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
Objet [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) qui représente le thread actif pour l’application qui contient le point d’arrêt.

`styleCondition`\
Valeur de l’énumération [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) décrivant le style de cette condition de point d’arrêt.

`bstrContext`\
Emplacement du point d’arrêt.

`bstrCondition`\
Condition de déclenchement du point d’arrêt.

`nRadix`\
Base à utiliser pour l’évaluation de toutes les informations numériques.

## <a name="remarks"></a>Notes
Cette structure est un membre des structures [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) et [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

Cette structure est également transmise en tant que paramètre aux méthodes [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) et [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md) .

## <a name="requirements"></a>Spécifications
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)
