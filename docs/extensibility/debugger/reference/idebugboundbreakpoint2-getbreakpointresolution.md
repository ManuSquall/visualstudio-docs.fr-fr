---
title: IDebugBoundBreakpoint2::GetBreakpointResolution (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::GetBreakpointResolution
helpviewer_keywords:
- GetBreakpointResolution method
- IDebugBoundBreakpoint2::GetBreakpointResolution method
ms.assetid: 4479ac61-18a9-4a30-b213-9921c5af9a26
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab88009eb1c1bbbd59bbad2dfcbf62567db3941f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735576"
---
# <a name="idebugboundbreakpoint2getbreakpointresolution"></a>IDebugBoundBreakpoint2::GetBreakpointResolution
Obtient la résolution de point d’arrêt qui décrit ce point d’arrêt.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetBreakpointResolution( 
    IDebugBreakpointResolution2** ppBPResolution
);
```

```csharp
int GetBreakpointResolution( 
    out IDebugBreakpointResolution2 ppBPResolution
);
```

## <a name="parameters"></a>Paramètres
`ppBPResolution`\
[out] Retourne l’interface [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) qui représente l’une des suivantes :

- L’objet de résolution de point de rupture qui décrit l’emplacement dans le code où un point de rupture de code a été lié.

- L’emplacement des données où un point de rupture de données a été lié.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Retourne `E_BP_DELETED` si l’état de l’objet `BPS_DELETED` de rupture lié est réglé (une partie du [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) énumération).

## <a name="remarks"></a>Notes
Appelez la méthode [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) pour déterminer si la résolution du point de rupture est pour le code ou les données.

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un objet simple `CBoundBreakpoint` qui expose [l’interface IDebugBoundBreakpoint2.](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)

```
HRESULT CBoundBreakpoint::GetBreakpointResolution(
    IDebugBreakpointResolution2** ppBPResolution)
{
    HRESULT hr;

    if (ppBPResolution)
    {
        // Verify that the bound breakpoint has not been deleted. If
        // deleted, then return hr = E_BP_DELETED.
        if (m_state != BPS_DELETED)
        {
            // Query for the IDebugBreakpointResolution2 interface.
            hr = m_pBPRes->QueryInterface(IID_IDebugBreakpointResolution2,
                                          (void **)ppBPResolution);
            assert(hr == S_OK);
        }
        else
        {
            hr = E_BP_DELETED;
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)
