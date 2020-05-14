---
title: MACHINE_INFO Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO
helpviewer_keywords:
- MACHINE_INFO structure
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad66992bd07afa2ef563c1b58fab0172e9a6121e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714545"
---
# <a name="machine_info"></a>MACHINE_INFO
Décrit une machine particulière.

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
 Une combinaison de drapeaux de [l’MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) recensement qui précisent quels champs de la structure sont paraséminés.

 `bstrName`\
 Nom de l’ordinateur. Équivalent à appeler [GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md).

 `Flags`\
 Une combinaison de drapeaux de [l’énumération MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) décrivant les attributs de la machine.

## <a name="remarks"></a>Notes
 Cette structure est retournée par un appel à la méthode [GetMachineInfo.](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
