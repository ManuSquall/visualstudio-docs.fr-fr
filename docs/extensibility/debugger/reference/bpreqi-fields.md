---
title: BPREQI_FIELDS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c0e10b6c253c61a9e68e0cf161201f7d2520ae6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737751"
---
# <a name="bpreqi_fields"></a>BPREQI_FIELDS
Spécifie les informations à récupérer au sujet d’une demande de point d’arrêt.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
typedef DWORD BPREQI_FIELDS;
```

```csharp
public enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
```

## <a name="fields"></a>Champs
`BPREQI_BPLOCATION`\
Initialiser/utiliser `bpLocation` le champ (emplacement de point d’arrêt) de la structure [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ou [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

`BPREQI_LANGUAGE`\
Initialiser/utiliser `guidLanguage` le champ `BP_REQUEST_INFO` `BP_REQUEST_INFO2` de la structure ou de la structure.

`BPREQI_PROGRAM`\
Initialiser/utiliser `pProgram` le champ `BP_REQUEST_INFO` `BP_REQUEST_INFO2` de la structure ou de la structure.

`BPREQI_PROGRAMNAME`\
Initialiser/utiliser `bstrProgramName` le champ `BP_REQUEST_INFO` `BP_REQUEST_INFO2` de la structure ou de la structure.

`BPREQI_THREAD`\
Initialiser/utiliser `pThread` le champ `BP_REQUEST_INFO` `BP_REQUEST_INFO2` de la structure ou de la structure.

`BPREQI_THREADNAME`\
Initialiser/utiliser `bstrThreadName` le champ `BP_REQUEST_INFO` `BP_REQUEST_INFO2` de la structure ou de la structure.

`BPREQI_PASSCOUNT`\
Initialiser/utiliser `bpPassCount` le champ `BP_REQUEST_INFO` `BP_REQUEST_INFO2` de la structure ou de la structure.

`BPREQI_CONDITION`\
Initialiser/utiliser `bpCondition` le champ (état de `BP_REQUEST_INFO` `BP_REQUEST_INFO2` rupture) de la structure ou.

`BPREQI_FLAGS`\
Initialiser/utiliser `dwFlags` le champ `BP_REQUEST_INFO` `BP_REQUEST_INFO2` de la structure ou de la structure.

`BPREQI_ALLOLDFIELDS`\
Initialiser/utiliser tous les champs `BP_REQUEST_INFO` pour la structure.

`BPREQI_VENDOR`\
Initialiser/utiliser `guidVendor` le `BP_REQUEST_INFO2` champ de structure.

`BPREQI_CONSTRAINT`\
Initialiser/utiliser `bstrConstraint` le `BP_REQUEST_INFO2` champ de structure.

`BPREQI_TRACEPOINT`\
Initialiser/utiliser `bstrTracepoint` le `BP_REQUEST_INFO2` champ de structure.

`BPREQI_ALLFIELDS`\
Spécifie tous `BP_REQUEST_INFO2` les champs pour la structure.

## <a name="remarks"></a>Notes
Passé comme argument au [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) et [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) méthodes pour préciser quels domaines des structures [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) et [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) doivent être paralés.

Ces drapeaux sont également utilisés pour `BP_REQUEST_INFO` `BP_REQUEST_INFO2` indiquer quels champs de la structure et les structures sont utilisés et valides lorsque chaque structure est retournée.

Ces valeurs peuvent être combinées avec un peu plus. `OR`

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
