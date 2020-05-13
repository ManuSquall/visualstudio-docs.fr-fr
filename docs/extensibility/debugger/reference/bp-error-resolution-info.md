---
title: BP_ERROR_RESOLUTION_INFO Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d48c4bc888db0ad8be6a0d6e98eeea2223a27e8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738089"
---
# <a name="bp_error_resolution_info"></a>BP_ERROR_RESOLUTION_INFO
Décrit la résolution d’un point d’erreur, y compris l’emplacement, le programme et le thread.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _BP_ERROR_RESOLUTION_INFO {
    BPERESI_FIELDS         dwFields;
    BP_RESOLUTION_LOCATION bpResLocation;
    IDebugProgram2*        pProgram;
    IDebugThread2*         pThread;
    BSTR                   bstrMessage;
    BP_ERROR_TYPE          dwType;
} BP_ERROR_RESOLUTION_INFO;
```

```csharp
public struct BP_ERROR_RESOLUTION_INFO {
    public uint                   dwFields;
    public BP_RESOLUTION_LOCATION bpResLocation;
    public IDebugProgram2         pProgram;
    public IDebugThread2          pThread;
    public string                 bstrMessage;
    public uint                   dwType;
};
```

## <a name="members"></a>Membres
`dwFields`\
Une combinaison de valeurs de [l’BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) énumération précisant quels domaines de cette structure sont remplis.

`bpResLocation`\
Le [syndicat BP_RESOLUTION_LOCATION,](../../../extensibility/debugger/reference/bp-resolution-location.md) qui précise le lieu de résolution des points d’arrêt.

`pProgram`\
[L’objet IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui représente l’application dans laquelle l’erreur de point d’arrêt s’est produite.

`pThread`\
[L’objet IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) qui représente le thread sur lequel l’application qui a généré l’erreur de point d’arrêt est en cours d’exécution.

`bstrMessage`\
Une chaîne contenant tout message d’avertissement ou d’erreur résultant de cette résolution d’erreurs.

`dwType`\
Une valeur de [l’énumération BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) qui spécifie le type d’erreur de point d’arrêt.

## <a name="remarks"></a>Notes
Cette structure est revenue de la méthode [GetResolutionInfo.](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)
