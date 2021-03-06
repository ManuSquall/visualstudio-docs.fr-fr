---
description: Spécifie le type d’informations à récupérer pour un ordinateur particulier.
title: MACHINE_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bb07f679027c37ebc74343ba17051a7e7980c1c7
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222560"
---
# <a name="machine_info_fields"></a>MACHINE_INFO_FIELDS
Spécifie le type d’informations à récupérer pour un ordinateur particulier.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
typedef DWORD MACHINE_INFO_FIELDS;
```

```csharp
public enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
```

## <a name="fields"></a>Champs
 `MCIF_NAME`\
 Initialisez/utilisez le `bstrName` champ de la structure.

 `MCIF_FLAGS`\
 Initialisez/utilisez le `Flags` champ de la structure.

 `MIF_ALL`\
 Initialisez/Utilisez tous les champs de la structure.

## <a name="remarks"></a>Notes
 Ces valeurs sont passées à la méthode [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) pour indiquer les membres de la structure [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) qui doivent être initialisés.

 Également utilisé dans le `Fields` membre de la `MACHINE_INFO` structure pour indiquer les champs qui sont utilisés et valides.

 Ces indicateurs peuvent être combinés avec une opération au niveau du bit `OR` .

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
