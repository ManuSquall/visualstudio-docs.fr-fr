---
title: BP_RESOLUTION_LOCATION Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b11d80e90daec19a14ca509e5a4b9bdb2d1ced4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737809"
---
# <a name="bp_resolution_location"></a>BP_RESOLUTION_LOCATION
Spécifie la structure de l’emplacement de résolution du point de rupture.

## <a name="syntax"></a>Syntaxe

```cpp
struct _BP_RESOLUTION_LOCATION {
    BP_TYPE bpType;
    union {
        BP_RESOLUTION_CODE bpresCode;
        BP_RESOLUTION_DATA bpresData;
        int                unused;
    } bpResLocation;
} BP_RESOLUTION_LOCATION;
```

```csharp
public struct BP_RESOLUTION_LOCATION {
    public uint   bpType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public uint   unionmember4;
};
```

## <a name="members"></a>Membres
`bpType`\
Une valeur du [recensement BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) qui précise comment interpréter le `bpResLocation` syndicat `unionmemberX` ou les membres.

`bpResLocation.bpresCode`\
[C seulement] Contient [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) la structure BP_RESOLUTION_CODE `bpType`  =  `BPT_CODE`si .

`bpResLocation.bpresData`\
[C seulement] Contient la structure [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) `bpType`  =  `BPT_DATA`si .

`bpResLocation.unused`\
[C seulement] Un placeholder.

`unionmember1`\
[C seulement] Voir Remarques sur la façon d’interpréter.

`unionmember2`\
[C seulement] Voir Remarques sur la façon d’interpréter.

`unionmember3`\
[C seulement] Voir Remarques sur la façon d’interpréter.

`unionmember4`\
[C seulement] Voir Remarques sur la façon d’interpréter.

## <a name="remarks"></a>Notes
Cette structure est membre des structures [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) et [BP_RESOLUTION_INFO.](../../../extensibility/debugger/reference/bp-resolution-info.md)

 [C seulement] Les `unionmemberX` membres sont interprétés selon le tableau suivant. Regardez la colonne de `bpType` gauche pour la `unionmemberX` valeur puis à `unionmemberX` travers pour déterminer ce que chaque membre représente et marshal le conséquence. Voir l’exemple pour une façon d’interpréter cette structure en C.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPT_DATA`|`string`(expression des données)|`string`(nom de la fonction)|`string`(nom d’image)|`enum_BP_RES_DATA_FLAGS`|

## <a name="example"></a>Exemple
Cet exemple montre comment `BP_RESOLUTION_LOCATION` interpréter la structure en C.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_RESOLUTION_LOCATION bprl)
        {
            if (bprl.bpType == (uint)enum_BP_TYPE.BPT_CODE)
            {
                IDebugCodeContext2 pContext = (IDebugCodeContext2)Marshal.GetObjectForIUnknown(bp.unionmember1);
            }
            else if (bprl.bpType == (uint)enum_BP_TYPE.BPT_DATA)
            {
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                string functionName = Marshal.PtrToStringBSTR(bp.unionmember2);
                string imageName = Marshal.PtrToStringBSTR(bp.unionmember3);
                enum_BP_RES_DATA_FLAGS numElements = (enum_BP_RES_DATA_FLAGS)bp.unionmember4;
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
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)
- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)
