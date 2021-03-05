---
description: Décrit le nombre et les conditions sur lesquelles un point d’arrêt conditionnel est déclenché.
title: BP_PASSCOUNT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT
helpviewer_keywords:
- BP_PASSCOUNT structure
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c1e44ede0f39b3d1b33967311365508da6a701d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144154"
---
# <a name="bp_passcount"></a>BP_PASSCOUNT
Décrit le nombre et les conditions sur lesquelles un point d’arrêt conditionnel est déclenché.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _BP_PASSCOUNT {
    DWORD              dwPassCount;
    BP_PASSCOUNT_STYLE stylePassCount;
} BP_PASSCOUNT;
```

```csharp
public struct BP_PASSCOUNT {
    public uint dwPassCount;
    public uint stylePassCount;
};
```

## <a name="members"></a>Membres
`dwPassCount`\
Nombre de fois où passer le point d’arrêt avant de le déclencher.

`stylePassCount`\
Valeur de l’énumération [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) qui spécifie le style du nombre de passes de point d’arrêt.

## <a name="remarks"></a>Notes
Cette structure est un membre de la structure [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) .

Cette structure est également transmise en tant que paramètre aux méthodes[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) et[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md) .

## <a name="requirements"></a>Configuration requise
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)
- [SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)
- [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)
