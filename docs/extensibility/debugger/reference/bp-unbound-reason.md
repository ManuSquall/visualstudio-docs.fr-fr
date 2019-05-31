---
title: BP_UNBOUND_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9de6812f3a61feca8ca8e7153fb281369c3312bd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350553"
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

## <a name="fields"></a>Champs
`BPUR_UNKNOWN`\
La raison est inconnue.

`BPUR_CODE_UNLOADED`\
Le code qui contient le point d’arrêt a été déchargé.

`BPUR_BREAKPOINT_REBIND`\
Le point d’arrêt a été reliée à un autre emplacement. Cela peut se produire après modification et continuer les opérations lorsque le point d’arrêt se déplace, ou lorsque le point d’arrêt est lié à un fichier avec un chemin d’accès qui n’est plus valide.

`BPUR_ BREAKPOINT_ERROR`\
Le point d’arrêt est déterminé comme étant erreur après que qu’il est lié. Cela se produit pour les points d’arrêt managés dont les conditions ne sont plus valides.

## <a name="remarks"></a>Notes
Retourné par la [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) (méthode).

## <a name="requirements"></a>Configuration requise
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
