---
description: Spécifie l’existence d’un point d’arrêt lié et spécifie également s’il est activé.
title: BP_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_STATE
helpviewer_keywords:
- BP_STATE enumeration
ms.assetid: 08aa6a3f-3e5f-4c83-8eca-7b7b5f8e208d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 886469727e9a20802f375faac12abbdd0d2b1ff2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089106"
---
# <a name="bp_state"></a>BP_STATE
Spécifie l’existence d’un point d’arrêt lié et spécifie également s’il est activé.

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
Spécifie qu’il n’existe aucun point d’arrêt.

`BPS_DELETED`\
Spécifie que le point d’arrêt a été supprimé.

`BPS_DISABLED`\
Spécifie que le point d’arrêt est désactivé.

`BPS_ENABLED`\
Spécifie que le point d’arrêt est activé.

## <a name="remarks"></a>Notes
Retourné par la méthode [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md) .

## <a name="requirements"></a>Spécifications
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)
