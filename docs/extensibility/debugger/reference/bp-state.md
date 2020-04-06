---
title: BP_STATE Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_STATE
helpviewer_keywords:
- BP_STATE enumeration
ms.assetid: 08aa6a3f-3e5f-4c83-8eca-7b7b5f8e208d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2721028c0635af274174574e4a264546c1909778
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737799"
---
# <a name="bp_state"></a>BP_STATE
Spécifie l’existence d’un point d’arrêt lié et précise également s’il est activé.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_BP_STATE {
    BPS_NONE     = 0x0000,
    BPS_DELETED  = 0x0001,
    BPS_DISABLED = 0x0002,
    BPS_ENABLED  = 0x0003
};
typedef DWORD BP_STATE;
```

```csharp
public enum enum_BP_STATE {
    BPS_NONE     = 0x0000,
    BPS_DELETED  = 0x0001,
    BPS_DISABLED = 0x0002,
    BPS_ENABLED  = 0x0003
};
```

## <a name="fields"></a>Champs
`BPS_NONE`\
Précise qu’il n’existe pas de point de rupture.

`BPS_DELETED`\
Spécifie que le point d’arrêt a été supprimé.

`BPS_DISABLED`\
Spécifie que le point d’arrêt est désactivé.

`BPS_ENABLED`\
Spécifie que le point d’arrêt est activé.

## <a name="remarks"></a>Notes
De retour de la méthode [GetState.](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetState (en)](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)
