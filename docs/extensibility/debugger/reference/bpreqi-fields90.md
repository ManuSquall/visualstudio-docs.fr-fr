---
title: BPREQI_FIELDS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be07e034b4059ae7ade40a5a248c01bc4a8237b8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695932"
---
# <a name="bpreqifields90"></a>BPREQI_FIELDS90
Énumère les valeurs valides qui spécifient les informations à récupérer une demande de point d’arrêt. Cette énumération étend la [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) énumération.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
typedef DWORD BPREQI_FIELDS90;
```

```csharp
public enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
```

#### <a name="parameters"></a>Paramètres
Initialiser BPREQI90_BPLOCATION ou utilisez le `bpLocation` champ (emplacement de point d’arrêt) de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ou [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) structure.

Initialiser BPREQI90_LANGUAGE ou utilisez le `guidLanguage` champ la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.

Initialiser BPREQI90_PROGRAM ou utilisez le `pProgram` champ la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.

Initialiser BPREQI90_PROGRAMNAME ou utilisez le `bstrProgramName` champ la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.

Initialiser BPREQI90_THREAD ou utilisez le `pThread` champ la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.

Initialiser BPREQI90_THREADNAME ou utilisez le `bstrThreadName` champ la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.

Initialiser BPREQI90_PASSCOUNT ou utilisez le `bpPassCount` champ la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.

Initialiser BPREQI90_CONDITION ou utilisez le `bpCondition` champ (condition de point d’arrêt) de la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.

Initialiser BPREQI90_FLAGS ou utilisez le `dwFlags` champ la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.

Initialiser BPREQI90_ALLOLDFIELDS ou l’utilisation de tous les champs pour la de la `BP_REQUEST_INFO` structure.

Initialiser BPREQI90_VENDOR ou utilisez le `guidVendor` champ `BP_REQUEST_INFO2` structure.

Initialiser BPREQI90_CONSTRAINT ou utilisez le `bstrConstraint` champ `BP_REQUEST_INFO2` structure.

Initialiser BPREQI90_TRACEPOINT ou utilisez le `bstrTracepoint` champ `BP_REQUEST_INFO2` structure.

Initialiser BPREQI90_MACROTRACEPOINT ou utilisez le `bstrMacroTracepoint` champ `BP_REQUEST_INFO2` structure. BPREQI_ALLFIELDS n’inclut pas ce champ.

BPREQI90_ALLFIELDS Spécifie tous les champs pour le `BP_REQUEST_INFO2` structure.

## <a name="requirements"></a>Spécifications
En-tête : Msdbg90.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
