---
description: Contient les informations requises pour implémenter un point d’arrêt, y compris le GUID du fournisseur, la contrainte et le point de trace.
title: BP_REQUEST_INFO2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO2
helpviewer_keywords:
- BP_REQUEST_INFO2 structure
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1efeceb42d45822f232e5a2e5e2fbe33f9996e34
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144115"
---
# <a name="bp_request_info2"></a>BP_REQUEST_INFO2
Contient les informations requises pour implémenter un point d’arrêt, y compris le GUID du fournisseur, la contrainte et le point de trace.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _BP_REQUEST_INFO2 {
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
} BP_REQUEST_INFO2;
```

```csharp
public struct BP_REQUEST_INFO2 {
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
Combinaison d’indicateurs de l’énumération [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) qui spécifie les champs à remplir.

`guidLanguage`\
GUID de la langue.

`bpLocation`\
Structure [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) qui spécifie le type de l’emplacement du point d’arrêt.

`pProgram`\
Objet [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui représente l’application dans laquelle le point d’arrêt se produit.

`bstrProgramName`\
Nom de l’application dans laquelle le point d’arrêt se produit.

`pThread`\
Objet [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) qui représente le thread dans lequel le point d’arrêt se produit.

`bstrThreadName`\
Nom du thread dans lequel le point d’arrêt se produit.

`bpCondition`\
Structure [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) qui décrit les conditions dans lesquelles le point d’arrêt est déclenché.

`bpPassCount`\
Structure [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) qui contient les informations sur le nombre de passes du point d’arrêt.

`dwFlags`\
Combinaison d’indicateurs de l’énumération [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) qui spécifie les indicateurs pour le point d’arrêt demandé.

`guidVendor`\
GUID du fournisseur. Peut être une valeur null.

`bstrConstraint`\
Nom de la contrainte de point d’arrêt. Peut être une valeur null.

`bstrTracepoint`\
Nom du point de trace. Peut être une valeur null.

## <a name="remarks"></a>Notes
Cette structure est retournée par la méthode [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md) .

## <a name="requirements"></a>Configuration requise
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

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
