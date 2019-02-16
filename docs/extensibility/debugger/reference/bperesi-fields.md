---
title: BPERESI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5877bc3fa7fb2844030a862a0a8f8244cffdbb6d
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56317547"
---
# <a name="bperesifields"></a>BPERESI_FIELDS
Spécifie les informations à récupérer sur la résolution d’un point d’arrêt ayant échouée.

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

## <a name="members"></a>Membres
PERESI_BPRESLOCATION  
Initialize/utiliser le `bpResLocation` champ (emplacement de résolution de point d’arrêt) de la [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) structure.

BPERESI_PROGRAM  
Initialize/utiliser le `pProgram` champ la `BP_ERROR_RESOLUTION_INFO` structure.

BPERESI_THREAD  
Initialize/utiliser le `pThread` champ la `BP_ERROR_RESOLUTION_INFO` structure.

BPERESI_MESSAGE  
Initialize/utiliser le `bstrMessage` champ la `BP_ERROR_RESOLUTION_INFO` structure.

BPERESI_TYPE  
Initialize/utiliser le `dwType` champ (type de point d’arrêt) de la `BP_ERROR_RESOLUTION_INFO` structure.

BPERESI_ALLFIELDS  
Initialize/utiliser tous les champs de la `BP_ERROR_RESOLUTION_INFO` structure.

## <a name="remarks"></a>Notes
Passé en tant que paramètre à la [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) méthode pour indiquer les champs de la [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) structure doivent être initialisées.

Ces valeurs sont également utilisées pour indiquer les champs dans le `BP_ERROR_RESOLUTION_INFO` structure sont utilisées et valide lors de cette structure est retournée.

Ces valeurs peuvent être combinées avec un opérateur de bits `OR`.

## <a name="requirements"></a>Spécifications
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
[Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)  
[GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
