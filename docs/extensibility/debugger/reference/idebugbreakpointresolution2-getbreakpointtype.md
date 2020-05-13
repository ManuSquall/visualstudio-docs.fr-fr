---
title: IDebugBreakpointResolution2::GetBreakpointType ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointResolution2::GetBreakpointType
helpviewer_keywords:
- IDebugBreakpointResolution2::GetBreakpointType
ms.assetid: 2b707fb9-f703-4c78-91bf-7434f57790a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2949366eeb3e79a732e94a4a8f8e9912048c6452
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734808"
---
# <a name="idebugbreakpointresolution2getbreakpointtype"></a>IDebugBreakpointResolution2::GetBreakpointType
Obtient le type de point d’arrêt représenté par cette résolution.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetBreakpointType( 
    BP_TYPE* pBPType
);
```

```csharp
int GetBreakpointType( 
    out enum_ BP_TYPE pBPType
);
```

## <a name="parameters"></a>Paramètres
`pBPType`\
[out] Retourne une valeur de [l’énumération BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) qui spécifie le type de ce point d’arrêt.

## <a name="return-value"></a>Valeur de retour
En cas `S_OK`de succès, les retours; renvoie autrement un code d’erreur. Retourne E_FAIL si le `bpResLocation` champ dans la structure [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) associée n’est pas valide.

## <a name="remarks"></a>Notes
Le point d’arrêt peut être un code ou un point d’arrêt de données, par exemple.

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un objet simple `CDebugBreakpointResolution` qui expose [l’interface IDebugBreakpointResolution2.](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)

```
HRESULT CDebugBreakpointResolution::GetBreakpointType(BP_TYPE* pBPType)
{
    HRESULT hr;

    if (pBPType)
    {
        // Set default BP_TYPE.
        *pBPType = BPT_NONE;

        // Check if the BPRESI_BPRESLOCATION flag is set in BPRESI_FIELDS.
        if (IsFlagSet(m_bpResolutionInfo.dwFields, BPRESI_BPRESLOCATION))
        {
            // Set the new BP_TYPE.
            *pBPType = m_bpResolutionInfo.bpResLocation.bpType;
            hr = S_OK;
        }
        else
        {
            hr = E_FAIL;
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
- [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
