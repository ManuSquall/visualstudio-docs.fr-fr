---
description: Spécifie les informations à récupérer à propos d’un échec de résolution d’un point d’arrêt.
title: BPERESI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8164f377e56c884149fb0711286d7702fe92eb82
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067684"
---
# <a name="bperesi_fields"></a>BPERESI_FIELDS
Spécifie les informations à récupérer à propos d’un échec de résolution d’un point d’arrêt.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
typedef DWORD BPERESI_FIELDS;
```

```csharp
public enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>Champs
`PERESI_BPRESLOCATION`\
Initialisez/utilisez le `bpResLocation` champ (emplacement de résolution des points d’arrêt) de la structure [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) .

`BPERESI_PROGRAM`\
Initialisez/utilisez le `pProgram` champ de la `BP_ERROR_RESOLUTION_INFO` structure.

`BPERESI_THREAD`\
Initialisez/utilisez le `pThread` champ de la `BP_ERROR_RESOLUTION_INFO` structure.

`BPERESI_MESSAGE`\
Initialisez/utilisez le `bstrMessage` champ de la `BP_ERROR_RESOLUTION_INFO` structure.

`BPERESI_TYPE`\
Initialisez/utilisez le `dwType` champ (type de point d’arrêt) de la `BP_ERROR_RESOLUTION_INFO` structure.

`BPERESI_ALLFIELDS`\
Initialisez/Utilisez tous les champs de la `BP_ERROR_RESOLUTION_INFO` structure.

## <a name="remarks"></a>Notes
Passé en tant que paramètre à la méthode [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) pour indiquer les champs de la structure [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) qui doivent être initialisés.

Ces valeurs sont également utilisées pour indiquer les champs de la `BP_ERROR_RESOLUTION_INFO` structure qui sont utilisés et valides lorsque cette structure est retournée.

Ces valeurs peuvent être combinées avec une opération de bits `OR` .

## <a name="requirements"></a>Spécifications
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
