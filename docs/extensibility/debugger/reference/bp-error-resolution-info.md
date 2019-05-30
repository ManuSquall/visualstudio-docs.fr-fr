---
title: BP_ERROR_RESOLUTION_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dca7dcac5dc7ccf4d30d9b61165771ba464bbcf9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351831"
---
# <a name="bperrorresolutioninfo"></a>BP_ERROR_RESOLUTION_INFO
Décrit la résolution d’un point d’arrêt erreur, y compris l’emplacement, de programme et de thread.

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
Une combinaison de valeurs à partir de la [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) énumération spécifiant les champs de cette structure sont remplis.

`bpResLocation`\
Le [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) union, qui spécifie l’emplacement de la résolution de point d’arrêt.

`pProgram`\
Le [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objet qui représente l’application dans laquelle l’erreur de point d’arrêt s’est produite.

`pThread`\
Le [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objet qui représente le thread sur lequel l’application qui a généré l’erreur de point d’arrêt est en cours d’exécution.

`bstrMessage`\
Chaîne contenant un message d’avertissement ou une erreur résultant de la résolution de cette erreur.

`dwType`\
Une valeur comprise entre le [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) énumération qui spécifie le type d’erreur de point d’arrêt.

## <a name="remarks"></a>Notes
Cette structure est retournée à partir de la [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) (méthode).

## <a name="requirements"></a>Configuration requise
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)
