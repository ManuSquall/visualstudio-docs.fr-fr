---
title: BP_LOCATION Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION
helpviewer_keywords:
- BP_LOCATION union
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c98fde516a3e836302cd7eb2c73abd730d5cc8c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737929"
---
# <a name="bp_location"></a>BP_LOCATION
Spécifie le type de structure utilisée pour décrire l’emplacement du point d’arrêt.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _BP_LOCATION {
    BP_LOCATION_TYPE bpLocationType;
    union {
        BP_LOCATION_CODE_FILE_LINE   bplocCodeFileLine;
        BP_LOCATION_CODE_FUNC_OFFSET bplocCodeFuncOffset;
        BP_LOCATION_CODE_CONTEXT     bplocCodeContext;
        BP_LOCATION_CODE_STRING      bplocCodeString;
        BP_LOCATION_CODE_ADDRESS     bplocCodeAddress;
        BP_LOCATION_DATA_STRING      bplocDataString;
        BP_LOCATION_RESOLUTION       bplocResolution;
        DWORD                        unused;
    } bpLocation;
} BP_LOCATION;
```

```csharp
public struct BP_LOCATION {
    public uint   bpLocationType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public IntPtr unionmember4;
};
```

## <a name="members"></a>Membres
`bpLocationType`\
Une valeur de [l’énumération BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) utilisée `bpLocation` pour interpréter `unionmemberX` le syndicat ou les membres.

`bpLocation`.`bplocCodeFileLine`\
[C seulement] Contient la structure [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) `bpLocationType`  =  `BPLT_CODE_FILE_LINE`si .

`bpLocation.bplocCodeFuncOffset`\
[C seulement] Contient la structure [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) `bpLocationType`  =  `BPLT_CODE_FUNC_OFFSET`si .

`bpLocation.bplocCodeContext`\
[C seulement] Contient la structure [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) `bpLocationType`  =  `BPLT_CODE_CONTEXT`si .

`bpLocation.bplocCodeString`\
[C seulement] Contient la structure [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) `bpLocationType`  =  `BPLT_CODE_STRING`si .

`bpLocation.bplocCodeAddress`\
[C seulement] Contient la structure [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) `bpLocationType`  =  `BPLT_CODE_ADDRESS`si .

`bpLocation.bplocDataString`\
[C seulement] Contient la structure [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) `bpLocationType`  =  `BPLT_DATA_STRING`si .

`bpLocation.bplocResolution`\
[C seulement] Contient [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) la structure BP_LOCATION_RESOLUTION `bpLocationType`  =  `BPLT_RESOLUTION`si .

`unionmember1`\
[C seulement] Voir Remarques sur la façon d’interpréter.

`unionmember2`\
[C seulement] Voir Remarques sur la façon d’interpréter.

`unionmember3`\
[C seulement] Voir Remarques sur la façon d’interpréter.

`unionmember4`\
[C seulement] Voir Remarques sur la façon d’interpréter.

## <a name="remarks"></a>Notes
Cette structure est membre des structures [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) et [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

 [C seulement] Les `unionmemberX` membres sont interprétés selon le tableau suivant. Regardez vers le bas `bpLocationType` de la colonne de gauche `unionmemberX` pour la valeur, puis regardez à travers les autres colonnes pour déterminer ce que chaque membre représente et marshal le `unionmemberX` conséquence. Voir l’exemple pour une façon d’interpréter une partie de cette structure en C.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPLT_CODE_FILE_LINE`|`string`(un contexte)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|
|`BPLT_CODE_FUNC_OFFSET`|`string`(un contexte)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPLT_CODE_STRING`|`string`(un contexte)|`string`(expression conditionnelle)|-|-|
|`BPLT_CODE_ADDRESS`|`string`(un contexte)|`string`(URL du module)|`string`(nom de la fonction)|`string`(adresse)|
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string`(un contexte)|`string`(expression des données)|`uint`(nombre d’éléments)|
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|

## <a name="example"></a>Exemple
Cet exemple montre comment `BP_LOCATION` interpréter la structure `BPLT_DATA_STRING` en C pour le type. Ce type particulier montre comment `unionmemberX` interpréter les quatre membres dans tous les formats possibles (objet, chaîne et nombre).

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_LOCATION bp)
        {
            if (bp.bpLocationType == (uint)enum_BP_LOCATION_TYPE.BPLT_DATA_STRING)
            {
                IDebugThread2 pThread = (IDebugThread2)Marshal.GetObjectForIUnknown(bp.unionmember1);
                string context = Marshal.PtrToStringBSTR(bp.unionmember2);
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                uint numElements = (uint)Marshal.ReadInt32(bp.unionmember4);
            }
        }
    }
}
```

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)
- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)
- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)
- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)
- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)
