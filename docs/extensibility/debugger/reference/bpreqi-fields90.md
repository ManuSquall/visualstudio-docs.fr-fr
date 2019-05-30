---
title: BPREQI_FIELDS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3f4d6df181ac15746202ae9f67e7b8874848e8f3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350546"
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

## <a name="fields"></a>Champs
`BPREQI90_BPLOCATION`\
Initialiser ou utiliser le `bpLocation` champ (emplacement de point d’arrêt) de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ou [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) structure.

`BPREQI90_LANGUAGE`\
Initialiser ou utiliser le `guidLanguage` champ la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.

`BPREQI90_PROGRAM`\
Initialiser ou utiliser le `pProgram` champ la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.

`BPREQI90_PROGRAMNAME`\
Initialiser ou utiliser le `bstrProgramName` champ la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.

`BPREQI90_THREAD`\
Initialiser ou utiliser le `pThread` champ la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.

`BPREQI90_THREADNAME`\
Initialiser ou utiliser le `bstrThreadName` champ la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.

`BPREQI90_PASSCOUNT`\
Initialiser ou utiliser le `bpPassCount` champ la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.

`BPREQI90_CONDITION`\
Initialiser ou utiliser le `bpCondition` champ (condition de point d’arrêt) de la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.

`BPREQI90_FLAGS`\
Initialiser ou utiliser le `dwFlags` champ la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.

`BPREQI90_ALLOLDFIELDS`\
Initialiser ou utiliser tous les champs pour la de la `BP_REQUEST_INFO` structure.

`BPREQI90_VENDOR`\
Initialiser ou utiliser le `guidVendor` champ `BP_REQUEST_INFO2` structure.

`BPREQI90_CONSTRAINT`\
Initialiser ou utiliser le `bstrConstraint` champ `BP_REQUEST_INFO2` structure.

`BPREQI90_TRACEPOINT`\
Initialiser ou utiliser le `bstrTracepoint` champ `BP_REQUEST_INFO2` structure.

`BPREQI90_MACROTRACEPOINT`\
Initialiser ou utiliser le `bstrMacroTracepoint` champ `BP_REQUEST_INFO2` structure. BPREQI_ALLFIELDS n’inclut pas ce champ.

`BPREQI90_ALLFIELDS`\
Spécifie tous les champs pour le `BP_REQUEST_INFO2` structure.

## <a name="requirements"></a>Configuration requise
En-tête : Msdbg90.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
