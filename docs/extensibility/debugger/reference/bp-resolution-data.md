---
title: BP_RESOLUTION_DATA Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_DATA
helpviewer_keywords:
- BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93a78f84c10af047e596459b68211b885d3c3085
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737843"
---
# <a name="bp_resolution_data"></a>BP_RESOLUTION_DATA
Décrit le résultat de la liaison d’un point d’arrêt des données.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _BP_RESOLUTION_DATA {
    BSTR              bstrDataExpr;
    BSTR              bstrFunc;
    BSTR              bstrImage;
    BP_RES_DATA_FLAGS dwFlags;
} BP_RESOLUTION_DATA;
```

```csharp
public struct BP_RESOLUTION_DATA {
    public string bstrDataExpr;
    public string bstrFunc;
    public string bstrImage;
    public uint   dwFlags;
};
```

## <a name="members"></a>Membres
`bstrDataExpr`\
L’expression des données qui a été liée.

`bstrFunc`\
Le nom de la fonction dans laquelle le point d’arrêt des données est lié (le cas échéant).

`bstrImage`\
Le nom du module (MyModule.dll, par exemple) que le point de rupture de données a lié.

`dwFlags`\
Une valeur de [l’énumération BP_RES_DATA_FLAGS,](../../../extensibility/debugger/reference/bp-res-data-flags.md) décrivant comment le point d’arrêt des données est implémenté.

## <a name="remarks"></a>Notes
Cette structure est membre de la structure [BP_RESOLUTION_LOCATION,](../../../extensibility/debugger/reference/bp-resolution-location.md) qui est à son tour un membre de la structure [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) retournée par la méthode [GetResolutionInfo.](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
