---
title: BP_CONDITION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e20db594fcc00f641634bfaae8d5342d4b520d7f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337425"
---
# <a name="bpcondition"></a>BP_CONDITION
Décrit les conditions sous lesquelles un point d’arrêt se déclenche.

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
Le [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objet qui représente le thread actif pour l’application qui contient le point d’arrêt.

`styleCondition`\
Une valeur comprise entre le [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) énumération décrivant le style de cette condition de point d’arrêt.

`bstrContext`\
L’emplacement du point d’arrêt.

`bstrCondition`\
La condition de déclenchement du point d’arrêt.

`nRadix`\
Base à utiliser lors de l’évaluation de toutes les informations numériques.

## <a name="remarks"></a>Notes
Cette structure est un membre de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) et [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) structures.

Cette structure est également passée en tant que paramètre à la [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) et [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md) méthodes.

## <a name="requirements"></a>Configuration requise
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)
