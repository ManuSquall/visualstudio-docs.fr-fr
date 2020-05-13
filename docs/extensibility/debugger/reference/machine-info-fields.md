---
title: MACHINE_INFO_FIELDS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 89a2552bb6a8bea88f54a897b829ab89b30ff413
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714525"
---
# <a name="machine_info_fields"></a>MACHINE_INFO_FIELDS
Précise le type d’information à récupérer pour une machine particulière.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
typedef DWORD MACHINE_INFO_FIELDS;
```

```csharp
public enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
```

## <a name="fields"></a>Champs
 `MCIF_NAME`\
 Initialiser/utiliser `bstrName` le champ dans la structure.

 `MCIF_FLAGS`\
 Initialiser/utiliser `Flags` le champ dans la structure.

 `MIF_ALL`\
 Initialiser/utiliser tous les champs de la structure.

## <a name="remarks"></a>Notes
 Ces valeurs sont transmises à la méthode [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) pour indiquer quels membres de la structure [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) doivent être parasécisés.

 Également utilisé `Fields` dans le `MACHINE_INFO` membre de la structure pour indiquer quels champs sont utilisés et valides.

 Ces drapeaux peuvent être combinés avec un peu plus. `OR`

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
