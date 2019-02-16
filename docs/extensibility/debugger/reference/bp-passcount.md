---
title: BP_PASSCOUNT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_PASSCOUNT
helpviewer_keywords:
- BP_PASSCOUNT structure
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d51e0fc895c104c1a18ef079c6784384e4cedbb4
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56316689"
---
# <a name="bppasscount"></a>BP_PASSCOUNT
Décrit le nombre et les conditions sur lequel un point d’arrêt conditionnel est déclenché.

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
`dwPassCount`  
Le nombre de fois à passer sur le point d’arrêt avant de déclencher l’il.

`stylePassCount`  
Une valeur comprise entre le [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) énumération qui spécifie le style du point d’arrêt passer le nombre.

## <a name="remarks"></a>Notes
Cette structure est un membre de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) structure.

Cette structure est également passée en tant que paramètre à la[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) et[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md) méthodes.

## <a name="requirements"></a>Spécifications
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
[Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)  
[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)  
[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)  
[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)  
[BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)
