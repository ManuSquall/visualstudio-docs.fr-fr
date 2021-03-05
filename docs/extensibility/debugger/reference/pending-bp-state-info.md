---
description: Contient des informations sur l’état d’un point d’arrêt qui est prêt à être lié à un emplacement de code.
title: PENDING_BP_STATE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: edd4bbdde1c241d90329343be1fd5570129c675a
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223925"
---
# <a name="pending_bp_state_info"></a>PENDING_BP_STATE_INFO
Contient des informations sur l’état d’un point d’arrêt qui est prêt à être lié à un emplacement de code.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _tagPENDING_BP_STATE_INFO { 
   PENDING_BP_STATE       state;
   PENDING_BP_STATE_FLAGS flags;
} PENDING_BP_STATE_INFO;
```

```csharp
public struct PENDING_BP_STATE_INFO { 
   public uint state;
   public uint flags;
};
```

## <a name="members"></a>Membres
 `state`\
 Valeur de l’énumération [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) qui spécifie l’état du point d’arrêt en attente.

 `flags`\
 Combinaison d’indicateurs de l’énumération [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) qui spécifie si le point d’arrêt est virtualisé.

## <a name="remarks"></a>Notes
 Cette structure est transmise à la méthode [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) où elle est remplie.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)
- [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)
- [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)
