---
title: IDebugBreakpointBoundEvent2::EnumBoundBreakpoints (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
helpviewer_keywords:
- IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
ms.assetid: 1f588feb-522e-488d-be92-7bc19b9e3688
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2f208c52bd45953aaad9efab9b6b65b15b3b759c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735357"
---
# <a name="idebugbreakpointboundevent2enumboundbreakpoints"></a>IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
Crée un enumérateur de points d’arrêt qui ont été liés sur cet événement.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumBoundBreakpoints( 
    IEnumDebugBoundBreakpoints2** ppEnum
);
```

```csharp
int EnumBoundBreakpoints( 
    out IEnumDebugBoundBreakpoints2 ppEnum
);
```

## <a name="parameters"></a>Paramètres
`ppEnum`\
[out] Retourne un objet [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) qui énumère tous les points d’arrêt liés à cet événement.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK`. Retours `S_FALSE` s’il n’y a pas de points d’arrêt consolidés; autrement, renvoie un code d’erreur.

## <a name="remarks"></a>Notes
La liste des points d’arrêt liés est pour ceux liés à cet événement et pourrait ne pas être la liste complète des points de rupture liés à partir d’un point d’arrêt en attente. Pour obtenir une liste de tous les points d’arrêt liés à un point d’arrêt en attente, appelez la méthode [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) pour obtenir l’objet [IDebugPendingBreakpoint2 associé,](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) puis appelez la méthode [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) pour obtenir un objet [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) qui contient tous les points de rupture liés pour le point d’arrêt en attente.

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un objet **CBreakpointSetDebugEventBase** qui expose [l’interface IDebugBreakpointBoundEvent2.](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)

```cpp
STDMETHODIMP CBreakpointSetDebugEventBase::EnumBoundBreakpoints(
    IEnumDebugBoundBreakpoints2 **ppEnum)
{
    HRESULT hRes = E_FAIL;

    if ( ppEnum )
    {
        if ( m_pEnumBound )
        {
            hRes = m_pEnumBound->Clone(ppEnum);

            if ( EVAL(S_OK == hRes) )
                (*ppEnum)->Reset();
        }
        else
            hRes = E_FAIL;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
