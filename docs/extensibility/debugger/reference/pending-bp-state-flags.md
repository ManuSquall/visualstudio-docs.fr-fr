---
title: PENDING_BP_STATE_FLAGS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE_FLAGS
helpviewer_keywords:
- PENDING_BP_STATE_FLAGS enumeration
ms.assetid: 85522449-3fd8-4da5-b0fe-a43160e0c33b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6da1a956ac958a95dd0c433283a71af0a9b29d1e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714091"
---
# <a name="pending_bp_state_flags"></a>PENDING_BP_STATE_FLAGS
Spécifie les drapeaux d’état de point d’arrêt en attente.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_PENDING_BP_STATE_FLAGS { 
   PBPSF_NONE        = 0x0000,
   PBPSF_VIRTUALIZED = 0x0001
};
typedef DWORD PENDING_BP_STATE_FLAGS;
```

```csharp
public enum enum_PENDING_BP_STATE_FLAGS { 
   PBPSF_NONE        = 0x0000,
   PBPSF_VIRTUALIZED = 0x0001
};
```

## <a name="fields"></a>Champs
 `PBPSF_NONE`Espace réservé.

 `PBPSF_VIRTUALIZED`Spécifie un point d’arrêt virtualisé en attente, qui doit être lié chaque fois que le nouveau code est chargé.

## <a name="remarks"></a>Notes
 Utilisé pour `flags` le membre de la structure [PENDING_BP_STATE_INFO.](../../../extensibility/debugger/reference/pending-bp-state-info.md)

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)
