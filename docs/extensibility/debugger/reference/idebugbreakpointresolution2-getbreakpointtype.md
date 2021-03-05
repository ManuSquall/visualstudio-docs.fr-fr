---
description: Obtient le type du point d’arrêt représenté par cette résolution.
title: 'IDebugBreakpointResolution2 :: GetBreakpointType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointResolution2::GetBreakpointType
helpviewer_keywords:
- IDebugBreakpointResolution2::GetBreakpointType
ms.assetid: 2b707fb9-f703-4c78-91bf-7434f57790a0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cca069871c99c623119853f37d1c422125b985ff
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158512"
---
# <a name="idebugbreakpointresolution2getbreakpointtype"></a>IDebugBreakpointResolution2::GetBreakpointType
Obtient le type du point d’arrêt représenté par cette résolution.

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
à Retourne une valeur de l’énumération [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) qui spécifie le type de ce point d’arrêt.

## <a name="return-value"></a>Valeur renvoyée
En cas de réussite, retourne `S_OK` ; sinon, retourne un code d’erreur. Retourne E_FAIL si le `bpResLocation` champ de la structure de [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) associée n’est pas valide.

## <a name="remarks"></a>Notes
Le point d’arrêt peut être un code ou un point d’arrêt de données, par exemple.

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un `CDebugBreakpointResolution` objet simple qui expose l’interface [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) .

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
