---
description: Décrit un ordinateur particulier.
title: MACHINE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO
helpviewer_keywords:
- MACHINE_INFO structure
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8a4b9686e5e3eb565b3c7b1c86a90ceac45b37cc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082346"
---
# <a name="machine_info"></a>MACHINE_INFO
Décrit un ordinateur particulier.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct tagMACHINE_INFO { 
   MACHINE_INFO_FIELDS Fields;
   BSTR                bstrName;
   MACHINE_INFO_FLAGS  Flags;
} MACHINE_INFO;
```

```csharp
public struct MACHINE_INFO { 
   public uint   Fields;
   public string bstrName;
   public uint   Flags;
};
```

## <a name="members"></a>Membres
 `Fields`\
 Combinaison d’indicateurs de l’énumération [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) qui spécifie les champs de la structure qui sont initialisés.

 `bstrName`\
 Nom de l’ordinateur. Équivalent à l’appel de [GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md).

 `Flags`\
 Combinaison d’indicateurs de l’énumération [MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) décrivant les attributs de l’ordinateur.

## <a name="remarks"></a>Notes
 Cette structure est retournée par un appel à la méthode [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) .

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
