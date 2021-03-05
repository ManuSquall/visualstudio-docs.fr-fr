---
description: Énumère les valeurs valides qui spécifient les informations à récupérer sur une demande de point d’arrêt.
title: BPREQI_FIELDS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5405f728cf979738de5a830421c4306c5e398bb2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151082"
---
# <a name="bpreqi_fields90"></a>BPREQI_FIELDS90
Énumère les valeurs valides qui spécifient les informations à récupérer sur une demande de point d’arrêt. Cette énumération étend l’énumération [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) .

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
Initialisez ou utilisez le `bpLocation` champ (emplacement du point d’arrêt) de la structure [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ou [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

`BPREQI90_LANGUAGE`\
Initialisez ou utilisez le `guidLanguage` champ de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` structure ou.

`BPREQI90_PROGRAM`\
Initialisez ou utilisez le `pProgram` champ de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` structure ou.

`BPREQI90_PROGRAMNAME`\
Initialisez ou utilisez le `bstrProgramName` champ de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` structure ou.

`BPREQI90_THREAD`\
Initialisez ou utilisez le `pThread` champ de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` structure ou.

`BPREQI90_THREADNAME`\
Initialisez ou utilisez le `bstrThreadName` champ de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` structure ou.

`BPREQI90_PASSCOUNT`\
Initialisez ou utilisez le `bpPassCount` champ de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` structure ou.

`BPREQI90_CONDITION`\
Initialisez ou utilisez le `bpCondition` champ (condition de point d’arrêt) de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` structure ou.

`BPREQI90_FLAGS`\
Initialisez ou utilisez le `dwFlags` champ de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` structure ou.

`BPREQI90_ALLOLDFIELDS`\
Initialisez ou utilisez tous les champs pour le de la `BP_REQUEST_INFO` structure.

`BPREQI90_VENDOR`\
Initialisez ou utilisez le `guidVendor` champ de la `BP_REQUEST_INFO2` structure.

`BPREQI90_CONSTRAINT`\
Initialisez ou utilisez le `bstrConstraint` champ de la `BP_REQUEST_INFO2` structure.

`BPREQI90_TRACEPOINT`\
Initialisez ou utilisez le `bstrTracepoint` champ de la `BP_REQUEST_INFO2` structure.

`BPREQI90_MACROTRACEPOINT`\
Initialisez ou utilisez le `bstrMacroTracepoint` champ de la `BP_REQUEST_INFO2` structure. BPREQI_ALLFIELDS n’inclut pas ce champ.

`BPREQI90_ALLFIELDS`\
Spécifie tous les champs de la `BP_REQUEST_INFO2` structure.

## <a name="requirements"></a>Configuration requise
En-tête : Msdbg90. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
