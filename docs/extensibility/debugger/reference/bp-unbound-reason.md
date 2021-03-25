---
description: Indique la raison pour laquelle un point d’arrêt a été indépendant.
title: BP_UNBOUND_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13f723c6395b8b271d6f097d811c5a31569c5853
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067697"
---
# <a name="bp_unbound_reason"></a>BP_UNBOUND_REASON
Indique la raison pour laquelle un point d’arrêt a été indépendant.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
typedef DWORD BP_UNBOUND_REASON;
```

```csharp
public enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
```

## <a name="fields"></a>Champs
`BPUR_UNKNOWN`\
La raison est inconnue.

`BPUR_CODE_UNLOADED`\
Le code qui contient le point d’arrêt a été déchargé.

`BPUR_BREAKPOINT_REBIND`\
Le point d’arrêt a été relié à un autre emplacement. Cela peut se produire après les opérations Modifier & Continuer au déplacement du point d’arrêt ou lorsque le point d’arrêt est lié à un fichier avec un chemin d’accès qui n’est plus valide.

`BPUR_ BREAKPOINT_ERROR`\
Le point d’arrêt est déterminé comme étant une erreur une fois qu’il est lié. Cela se produit dans les points d’arrêt gérés dont les conditions ne sont plus valides.

## <a name="remarks"></a>Notes
Retourné par la méthode [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) .

## <a name="requirements"></a>Spécifications
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
