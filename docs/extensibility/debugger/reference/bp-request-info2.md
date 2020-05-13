---
title: BP_REQUEST_INFO2 Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO2
helpviewer_keywords:
- BP_REQUEST_INFO2 structure
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04d1db2ca8176678d8a72a84ede2bddcbfa2f152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737878"
---
# <a name="bp_request_info2"></a>BP_REQUEST_INFO2
Contient les informations nécessaires à la mise en œuvre d’un point d’arrêt, y compris le fournisseur GUID, la contrainte et le point de traçabilité.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _BP_REQUEST_INFO2 {
    BPREQI_FIELDS   dwFields;
    GUID            guidLanguage;
    BP_LOCATION     bpLocation;
    IDebugProgram2* pProgram;
    BSTR            bstrProgramName;
    IDebugThread2*  pThread;
    BSTR            bstrThreadName;
    BP_CONDITION    bpCondition;
    BP_PASSCOUNT    bpPassCount;
    BP_FLAGS        dwFlags;
    GUID            guidVendor;
    BSTR            bstrConstraint;
    BSTR            bstrTracepoint;
} BP_REQUEST_INFO2;
```

```csharp
public struct BP_REQUEST_INFO2 {
    public uint           dwFields;
    public Guid           guidLanguage;
    public BP_LOCATION    bpLocation;
    public IDebugProgram2 pProgram;
    public string         bstrProgramName;
    public IDebugThread2  pThread;
    public string         bstrThreadName;
    public BP_CONDITION   bpCondition;
    public BP_PASSCOUNT   bpPassCount;
    public uint           dwFlags;
    public Guid           guidVendor;
    public string         bstrConstraint;
    public string         bstrTracepoint;
};
```

## <a name="members"></a>Membres
`dwFields`\
Une combinaison de drapeaux de [l’énumération BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) qui précise quels champs sont remplis.

`guidLanguage`\
GUID de la langue.

`bpLocation`\
La [structure BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) qui spécifie le type de point d’arrêt.

`pProgram`\
[L’objet IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui représente l’application dans laquelle le point d’arrêt se produit.

`bstrProgramName`\
Le nom de l’application dans laquelle le point d’arrêt se produit.

`pThread`\
[L’objet IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) qui représente le fil dans lequel le point d’arrêt se produit.

`bstrThreadName`\
Le nom du fil dans lequel le point d’arrêt se produit.

`bpCondition`\
La [structure BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) qui décrit les conditions dans lesquelles le point d’arrêt s’allumera.

`bpPassCount`\
La [structure BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) qui contient les informations de comptage de passage du point d’arrêt.

`dwFlags`\
Une combinaison de drapeaux de [l’BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) énumération qui spécifie les drapeaux pour le point d’arrêt demandé.

`guidVendor`\
GUID du vendeur. Peut être une valeur nulle.

`bstrConstraint`\
Nom de la contrainte de point d’arrêt. Peut être une valeur nulle.

`bstrTracepoint`\
Nom du point de trace. Peut être une valeur nulle.

## <a name="remarks"></a>Notes
Cette structure est retournée par la méthode [GetRequestInfo2.](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)
