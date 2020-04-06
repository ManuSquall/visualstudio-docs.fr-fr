---
title: IDebugBreakpointBoundEvent2::GetPendingBreakpoint (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointBoundEvent2::GetPendingBreakpoint
helpviewer_keywords:
- IDebugBreakpointBoundEvent2::GetPendingBreakpoint
ms.assetid: 6da7ed86-b412-4964-b6a3-0687a66f63fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 85c137445e2255a76f7fa3be2fb56e2579e578c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735257"
---
# <a name="idebugbreakpointboundevent2getpendingbreakpoint"></a>IDebugBreakpointBoundEvent2::GetPendingBreakpoint
Obtient le point d’arrêt en attente qui est lié.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPendingBreakpoint(
    IDebugPendingBreakpoint2** ppPendingBP
);
```

```cpp
int GetPendingBreakpoint(
    out IDebugPendingBreakpoint2 ppPendingBP
);
```

## <a name="parameters"></a>Paramètres
`ppPendingBP`\
[out] Retourne [l’objet IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) qui représente le point d’arrêt en attente étant lié.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un objet **CBreakpointSetDebugEventBase** qui expose [l’interface IDebugBreakpointBoundEvent2.](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)

```cpp
STDMETHODIMP CBreakpointSetDebugEventBase::GetPendingBreakpoint(
    IDebugPendingBreakpoint2 **ppPendingBP)
{
    HRESULT hRes = E_FAIL;

    if ( ppPendingBP )
    {
        if ( m_pPendingBP )
        {
            *ppPendingBP = m_pPendingBP;

            m_pPendingBP->AddRef();

            hRes = S_OK;
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
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
