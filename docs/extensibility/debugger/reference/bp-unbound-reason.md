---
title: BP_UNBOUND_REASON Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b0ee695e1108bf9f1c6069084a0826ee23bf37d4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737774"
---
# <a name="bp_unbound_reason"></a>BP_UNBOUND_REASON
Donne la raison pour laquelle un point d’arrêt n’était pas lié.

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
Le point d’arrêt a été rebondir à un endroit différent. Cela peut se produire après modifier et poursuivre les opérations lorsque le point d’arrêt se déplace, ou lorsque le point d’arrêt est lié à un fichier avec un chemin qui n’est plus valide.

`BPUR_ BREAKPOINT_ERROR`\
Le point d’arrêt est déterminé à être dans l’erreur après qu’il soit lié. Il arrive que les points d’arrêt gérés dont les conditions ne soient plus valables.

## <a name="remarks"></a>Notes
Retourné par la méthode [GetReason.](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
