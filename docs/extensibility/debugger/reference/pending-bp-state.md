---
description: Spécifie l’état d’un point d’arrêt en attente (un point d’arrêt qui n’a pas encore été lié).
title: PENDING_BP_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE
helpviewer_keywords:
- PENDING_BP_STATE enumeration
ms.assetid: ac04ad72-fa92-4a15-ade2-0d0bbbadfc7f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d041042be92fe68dd6f0ea35bbdb4f6dd6d9ac7e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086376"
---
# <a name="pending_bp_state"></a>PENDING_BP_STATE
Spécifie l’état d’un point d’arrêt en attente (un point d’arrêt qui n’a pas encore été lié).

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_PENDING_BP_STATE { 
   PBPS_NONE     = 0x0000,
   PBPS_DELETED  = 0x0001,
   PBPS_DISABLED = 0x0002,
   PBPS_ENABLED  = 0x0003
};
typedef DWORD PENDING_BP_STATE;
```

```csharp
public enum enum_PENDING_BP_STATE { 
   PBPS_NONE     = 0x0000,
   PBPS_DELETED  = 0x0001,
   PBPS_DISABLED = 0x0002,
   PBPS_ENABLED  = 0x0003
};
```

## <a name="fields"></a>Champs
 `PBPS_NONE`\
 Espace réservé pour zéro. Cette valeur n’est jamais retournée.

 `PBPS_DELETED`\
 Indique que le point d’arrêt en attente a été supprimé.

 `PBPS_DISABLED`\
 Indique que le point d’arrêt en attente est désactivé.

 `PBPS_ENABLED`\
 Indique que le point d’arrêt en attente est activé.

## <a name="remarks"></a>Notes
 Utilisez comme `state` membre de la structure [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) .

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)
