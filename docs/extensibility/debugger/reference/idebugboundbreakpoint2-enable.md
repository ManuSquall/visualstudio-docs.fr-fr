---
description: Active ou désactive le point d’arrêt.
title: 'IDebugBoundBreakpoint2 :: Enable | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::Enable
helpviewer_keywords:
- Enable method
- IDebugBoundBreakpoint2::Enable method
ms.assetid: 1b4e3f73-c94d-4aa3-9aa8-0d8cb8a6c5ca
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b7620af5091907557a0a90a0cf0f2b0e301938c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173925"
---
# <a name="idebugboundbreakpoint2enable"></a>IDebugBoundBreakpoint2::Enable
Active ou désactive le point d’arrêt.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Enable(
    BOOL fEnable
);
```

```csharp
int Enable( 
    int fEnable
);
```

## <a name="parameters"></a>Paramètres
`fEnable`\
dans Définissez sur une valeur différente de zéro ( `TRUE` ) pour activer ou sur zéro ( `FALSE` ) pour désactiver le point d’arrêt.

## <a name="return-value"></a>Valeur renvoyée
En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Retourne `E_BP_DELETED` si l’état de l’objet de point d’arrêt lié est défini sur `BPS_DELETED` (partie de l’énumération [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) ).

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un `CBoundBreakpoint` objet simple qui expose l’interface [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .

```
HRESULT CBoundBreakpoint::Enable(BOOL fEnable)
{
    HRESULT hr;

    // Verify that the bound breakpoint has not been deleted. If deleted,
    // then return hr = E_BP_DELETED.
    if (m_state != BPS_DELETED)
    {
        // Check the state of the bound breakpoint. If the breakpoint is
        // supposed to be, but has not already been, enabled, then have the
        // interpreter set the breakpoint.
        if (fEnable && m_state != BPS_ENABLED)
        {
            hr = m_pInterp->SetBreakpoint(m_sbstrDoc, this);
            if (hr == S_OK)
            {
                // Change the state of the breakpoint to BPS_ENABLED.
                m_state = BPS_ENABLED;
            }
        }
        // Check the state of the bound breakpoint. If the breakpoint is
        // supposed to be, but has not already been, disabled, then have the
        // interpreter remove the breakpoint.
        else if (!fEnable && m_state != BPS_DISABLED)
        {
            hr = m_pInterp->RemoveBreakpoint(m_sbstrDoc, this);
            if (hr == S_OK)
            {
                // Change the state of the breakpoint to BPS_DISABLED.
                m_state = BPS_DISABLED;
            }
        }
        else
        {
            hr = S_FALSE;
        }
    }
    else
    {
        hr = E_BP_DELETED;
    }

    return hr;
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
