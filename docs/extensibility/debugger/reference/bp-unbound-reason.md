---
title: BP_UNBOUND_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65393f6e162cb15ded7a0e598e360c7ce90bb3cd
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717661"
---
# <a name="bpunboundreason"></a>BP_UNBOUND_REASON
Donne la raison pour laquelle qu'un point d’arrêt a été dissocié.

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

## <a name="members"></a>Membres
BPUR_UNKNOWN la raison est inconnu.

BPUR_CODE_UNLOADED le code qui contient le point d’arrêt a été déchargé.

BPUR_BREAKPOINT_REBIND le point d’arrêt a été reconnectés vers un autre emplacement. Cela peut se produire après modification et continuer les opérations lorsque le point d’arrêt se déplace, ou lorsque le point d’arrêt est lié à un fichier avec un chemin d’accès qui n’est plus valide.

BPUR_ BREAKPOINT_ERROR le point d’arrêt est déterminé comme étant erreur après que qu’il est lié. Cela se produit pour les points d’arrêt managés dont les conditions ne sont plus valides.

## <a name="remarks"></a>Notes
Retourné par la [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) (méthode).

## <a name="requirements"></a>Spécifications
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
