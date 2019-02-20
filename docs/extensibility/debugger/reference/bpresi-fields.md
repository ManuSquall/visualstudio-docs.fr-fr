---
title: BPRESI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0784d26f4d5ae6bd8edd9b6565644a6cd513db78
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "56413057"
---
# <a name="bpresifields"></a>BPRESI_FIELDS
Spécifie les informations à récupérer sur la résolution d’un point d’arrêt.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
typedef DWORD BPRESI_FIELDS;
```

```csharp
public enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
```

## <a name="members"></a>Membres
BPRESI_BPRESLOCATION  
Initialize/utiliser le `bpResLocation` champ (emplacement de résolution de point d’arrêt) de la [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) structure.

BPRESI_PROGRAM  
Initialize/utiliser le `pProgram` champ la `BP_RESOLUTION_INFO` structure.

BPRESI_THREAD  
Initialize/utiliser le `pThread` champ la `BP_RESOLUTION_INFO` structure.

BPRESI_ALLFIELDS  
Spécifie tous les champs.

## <a name="remarks"></a>Notes
Passé à la [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) méthode pour indiquer les champs de la [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) structure doivent être initialisées.

Ces indicateurs sont également utilisées pour indiquer les champs de la `BP_RESOLUTION_INFO` structure sont utilisées et valide lors de cette structure est retournée.

Ces valeurs peuvent être combinées avec un opérateur de bits `OR`.

## <a name="requirements"></a>Spécifications
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
[Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)  
[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
