---
description: Décrit la résolution d’un point d’arrêt d’erreur, y compris l’emplacement, le programme et le thread.
title: BP_ERROR_RESOLUTION_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 44bf92db77bf39e7e4a214e902781e27a7a731ef
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085297"
---
# <a name="bp_error_resolution_info"></a>BP_ERROR_RESOLUTION_INFO
Décrit la résolution d’un point d’arrêt d’erreur, y compris l’emplacement, le programme et le thread.

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
Combinaison de valeurs de l’énumération [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) spécifiant les champs de cette structure à remplir.

`bpResLocation`\
[BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Union, qui spécifie l’emplacement de résolution du point d’arrêt.

`pProgram`\
Objet [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui représente l’application dans laquelle l’erreur de point d’arrêt s’est produite.

`pThread`\
Objet [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) qui représente le thread sur lequel l’application qui a généré l’erreur de point d’arrêt s’exécute.

`bstrMessage`\
Chaîne contenant un message d’avertissement ou d’erreur résultant de la résolution de cette erreur.

`dwType`\
Valeur de l’énumération [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) qui spécifie le type d’erreur de point d’arrêt.

## <a name="remarks"></a>Notes
Cette structure est retournée par la méthode [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) .

## <a name="requirements"></a>Spécifications
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)
