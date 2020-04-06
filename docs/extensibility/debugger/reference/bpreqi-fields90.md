---
title: BPREQI_FIELDS90 Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea46939118ec48490280d6a85cc84e144d320d4e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737737"
---
# <a name="bpreqi_fields90"></a>BPREQI_FIELDS90
Énumère les valeurs valides qui spécifient les informations à récupérer au sujet d’une demande de point d’arrêt. Cette énumération prolonge [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) la BPREQI_FIELDS’énumération.

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
Initialiser ou `bpLocation` utiliser le champ (emplacement de point d’arrêt) de la structure [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ou [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

`BPREQI90_LANGUAGE`\
Initialiser ou `guidLanguage` utiliser le `BP_REQUEST_INFO` `BP_REQUEST_INFO2` champ de la structure ou de la structure.

`BPREQI90_PROGRAM`\
Initialiser ou `pProgram` utiliser le `BP_REQUEST_INFO` `BP_REQUEST_INFO2` champ de la structure ou de la structure.

`BPREQI90_PROGRAMNAME`\
Initialiser ou `bstrProgramName` utiliser le `BP_REQUEST_INFO` `BP_REQUEST_INFO2` champ de la structure ou de la structure.

`BPREQI90_THREAD`\
Initialiser ou `pThread` utiliser le `BP_REQUEST_INFO` `BP_REQUEST_INFO2` champ de la structure ou de la structure.

`BPREQI90_THREADNAME`\
Initialiser ou `bstrThreadName` utiliser le `BP_REQUEST_INFO` `BP_REQUEST_INFO2` champ de la structure ou de la structure.

`BPREQI90_PASSCOUNT`\
Initialiser ou `bpPassCount` utiliser le `BP_REQUEST_INFO` `BP_REQUEST_INFO2` champ de la structure ou de la structure.

`BPREQI90_CONDITION`\
Initialiser ou `bpCondition` utiliser le champ (état `BP_REQUEST_INFO` `BP_REQUEST_INFO2` de rupture) de la structure ou.

`BPREQI90_FLAGS`\
Initialiser ou `dwFlags` utiliser le `BP_REQUEST_INFO` `BP_REQUEST_INFO2` champ de la structure ou de la structure.

`BPREQI90_ALLOLDFIELDS`\
Initialiser ou utiliser tous les `BP_REQUEST_INFO` champs pour la structure.

`BPREQI90_VENDOR`\
Initialiser ou `guidVendor` utiliser `BP_REQUEST_INFO2` le champ de structure.

`BPREQI90_CONSTRAINT`\
Initialiser ou `bstrConstraint` utiliser `BP_REQUEST_INFO2` le champ de structure.

`BPREQI90_TRACEPOINT`\
Initialiser ou `bstrTracepoint` utiliser `BP_REQUEST_INFO2` le champ de structure.

`BPREQI90_MACROTRACEPOINT`\
Initialiser ou `bstrMacroTracepoint` utiliser `BP_REQUEST_INFO2` le champ de structure. BPREQI_ALLFIELDS n’inclut pas ce domaine.

`BPREQI90_ALLFIELDS`\
Spécifie tous `BP_REQUEST_INFO2` les champs pour la structure.

## <a name="requirements"></a>Spécifications
En-tête: Msdbg90.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
