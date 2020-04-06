---
title: BP_PASSCOUNT Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT
helpviewer_keywords:
- BP_PASSCOUNT structure
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e3177ff093aea9a6f52465bd606b22883249d6b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737900"
---
# <a name="bp_passcount"></a>BP_PASSCOUNT
Décrit le nombre et les conditions auxquelles un point d’arrêt conditionnel est tiré.

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
Le nombre de fois pour passer au-dessus du point d’arrêt avant de le tirer.

`stylePassCount`\
Une valeur de [l’énumération BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) qui spécifie le style du nombre de laissez-passer de point d’arrêt.

## <a name="remarks"></a>Notes
Cette structure est membre de la structure [BP_REQUEST_INFO.](../../../extensibility/debugger/reference/bp-request-info.md)

Cette structure est également transmise comme paramètre aux méthodes[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) et[SetPassCount.](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)
- [SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)
- [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)
