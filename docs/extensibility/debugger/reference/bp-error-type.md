---
description: Spécifie le type d’erreur d’un point d’arrêt.
title: BP_ERROR_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ced08f5bf4cd51a1f89f139fd19971e21e2225e6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144427"
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
Ne spécifie aucune erreur de point d’arrêt.

`BPET_TYPE_WARNING`\
Spécifie une erreur de point d’arrêt de style avertissement.

`BPET_TYPE_ERROR`\
Spécifie une erreur de point d’arrêt de style erreur.

`BPET_SEV_HIGH`\
Spécifie une erreur de point d’arrêt de gravité élevée.

`BPET_SEV_GENERAL`\
Spécifie une erreur de point d’arrêt de gravité moyenne.

`BPET_SEV_LOW`\
Spécifie une erreur de point d’arrêt de faible gravité.

`BPET_TYPE_MASK`\
Spécifie une erreur de point d’arrêt de style masque.

`BPET_SEV_MASK`\
Spécifie une erreur de point d’arrêt de type de masque de gravité.

`BPET_GENERAL_WARNING`\
Spécifie une erreur de point d’arrêt de type avertissement général.

`BPET_GENERAL_ERROR`\
Spécifie une erreur de point d’arrêt de style erreur générale.

`BPET_ALL`\
Spécifie tous les types d’erreur de point d’arrêt.

## <a name="remarks"></a>Notes
Ces valeurs peuvent être combinées avec une opération de bits `OR` and utilisée pour le `dwType` membre de la structure [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) . Passé en tant que paramètre à la méthode [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) .

Un type d’erreur de point d’arrêt est composé d’un type et d’un niveau de gravité. Cela signifie qu’un type d’erreur de point d’arrêt n’est jamais simplement un type (par exemple, `BPET_TYPE_ERROR` ,) ou une gravité (par exemple, `BPET_SEV_GENERAL` ) par lui-même. `BPET_GENERAL_WARNING` et `BPET_GENERAL_ERROR` fournissent des valeurs prédéfinies pour les points d’arrêt d’avertissement et d’erreur généraux.

## <a name="requirements"></a>Configuration requise
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
