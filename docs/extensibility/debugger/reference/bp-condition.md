---
title: BP_CONDITION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8bbdcec09ef004817b05e7992ae72bc856764da9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945849"
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

## <a name="requirements"></a>Configuration requise
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
