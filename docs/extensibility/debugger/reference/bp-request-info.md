---
description: Contient les informations requises pour implémenter un point d’arrêt.
title: BP_REQUEST_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO
helpviewer_keywords:
- BP_REQUEST_INFO structure
ms.assetid: 42a31412-5b6b-47fe-a762-0c2bc769e1cc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 941c8302fa52d579c2fbefc62ccd962d26e2cf13
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144129"
---
# <a name="bp_request_info"></a>BP_REQUEST_INFO
Contient les informations requises pour implémenter un point d’arrêt.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _BP_REQUEST_INFO {
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
} BP_REQUEST_INFO;
```

```csharp
public struct BP_REQUEST_INFO {
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

## <a name="remarks"></a>Notes
Cette structure est retournée par la méthode [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) .

Si vous avez besoin d’obtenir le GUID du fournisseur du moteur de débogage, la contrainte de point d’arrêt ou le point de trace, consultez la structure [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

## <a name="requirements"></a>Configuration requise
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
