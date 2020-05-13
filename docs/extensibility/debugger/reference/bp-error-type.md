---
title: BP_ERROR_TYPE Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e777e1f8cb67187a81f8f3bb4f79299939bfa31c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738076"
---
# <a name="bp_error_type"></a>BP_ERROR_TYPE
Spécifie le type d’erreur d’un point d’arrêt.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
typedef DWORD BP_ERROR_TYPE;
```

```csharp
public enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
```

## <a name="fields"></a>Champs
`BPET_NONE`\
Spécifie aucune erreur de point de rupture.

`BPET_TYPE_WARNING`\
Spécifie une erreur de point de rupture de type avertissement.

`BPET_TYPE_ERROR`\
Spécifie une erreur de point de rupture de type erreur.

`BPET_SEV_HIGH`\
Spécifie une erreur de point de rupture de haute gravité.

`BPET_SEV_GENERAL`\
Spécifie une erreur de point de rupture de gravité moyenne.

`BPET_SEV_LOW`\
Spécifie une erreur de point de rupture de faible gravité.

`BPET_TYPE_MASK`\
Spécifie une erreur de point de rupture de type masque.

`BPET_SEV_MASK`\
Spécifie une erreur de point de rupture de type masque de sévérité.

`BPET_GENERAL_WARNING`\
Spécifie une erreur de point de rupture de type avertissement général.

`BPET_GENERAL_ERROR`\
Spécifie une erreur de point de rupture de type erreur générale.

`BPET_ALL`\
Spécifie tous les types d’erreurs de point de rupture.

## <a name="remarks"></a>Notes
Ces valeurs peuvent être combinées avec un peu plus sage `OR` et utilisé pour le `dwType` membre de la structure [BP_ERROR_RESOLUTION_INFO.](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Passé comme paramètre à la méthode [EnumErrorBreakpoints.](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)

Un type d’erreur de point de rupture est composé d’un type et d’une sévérité. Cela signifie qu’un type d’erreur de point `BPET_TYPE_ERROR`de rupture n’est `BPET_SEV_GENERAL`jamais seulement un type (par exemple, ,) ou une sévérité (par exemple, ) par lui-même. `BPET_GENERAL_WARNING`et `BPET_GENERAL_ERROR` fournir des valeurs prédéfinises pour les points d’avertissement général et d’erreur.

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
