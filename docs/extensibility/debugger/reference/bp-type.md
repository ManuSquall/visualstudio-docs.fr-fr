---
description: Spécifie si le point d’arrêt se trouve à un emplacement de code, si est un emplacement de données ou s’il s’agit d’un autre type de point d’arrêt.
title: BP_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_TYPE
helpviewer_keywords:
- BP_TYPE enumeration
ms.assetid: ef07191e-7966-43ab-96fb-1a0b1db3115d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 23f7b6c42b1c4736ba0eb76a451bb91e74ca5ff5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089093"
---
# <a name="bp_type"></a>BP_TYPE
Spécifie si le point d’arrêt se trouve à un emplacement de code, si est un emplacement de données ou s’il s’agit d’un autre type de point d’arrêt.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_BP_TYPE {
    BPT_NONE    = 0x0000,
    BPT_CODE    = 0x0001,
    BPT_DATA    = 0x0002,
    BPT_SPECIAL = 0x0003
};
typedef DWORD BP_TYPE;
```

```csharp
public enum enum_BP_TYPE {
    BPT_NONE    = 0x0000,
    BPT_CODE    = 0x0001,
    BPT_DATA    = 0x0002,
    BPT_SPECIAL = 0x0003
};
```

## <a name="fields"></a>Champs
`BPT_NONE`\
Ne spécifie aucun type de point d’arrêt.

`BPT_CODE`\
Spécifie un point d’arrêt de code.

`BPT_DATA`\
Spécifie un point d’arrêt sur variable.

`BPT_SPECIAL`\
Spécifie un point d’arrêt qui n’est ni un code ni un type de données. Ce type est déconseillé et ne doit pas être utilisé.

## <a name="remarks"></a>Notes
Passé en tant que paramètre aux méthodes [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) et [GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md) .

## <a name="requirements"></a>Spécifications
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)
