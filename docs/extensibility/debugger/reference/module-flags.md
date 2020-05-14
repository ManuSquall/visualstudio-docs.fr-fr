---
title: MODULE_FLAGS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 78c7f24d64ffca667706c3b2fcebeffad16a9d85
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714256"
---
# <a name="module_flags"></a>MODULE_FLAGS
Utilisé pour décrire un module.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_MODULE_FLAGS { 
   MODULE_FLAG_NONE        = 0x0000,
   MODULE_FLAG_SYSTEM      = 0x0001,
   MODULE_FLAG_SYMBOLS     = 0x0002,
   MODULE_FLAG_64BIT       = 0x0004,
   MODULE_FLAG_OPTIMIZED   = 0x0008,
   MODULE_FLAG_UNOPTIMIZED = 0x0010
};
typedef DWORD MODULE_FLAGS;
```

```csharp
public enum enum_MODULE_FLAGS { 
   MODULE_FLAG_NONE        = 0x0000,
   MODULE_FLAG_SYSTEM      = 0x0001,
   MODULE_FLAG_SYMBOLS     = 0x0002,
   MODULE_FLAG_64BIT       = 0x0004,
   MODULE_FLAG_OPTIMIZED   = 0x0008,
   MODULE_FLAG_UNOPTIMIZED = 0x0010
};
```

## <a name="fields"></a>Champs
 `MODULE_FLAG_NONE`\
 Spécifie aucun module.

 `MODULE_FLAG_SYSTEM`\
 Spécifie un module système.

 `MODULE_FLAG_SYMBOLS`\
 Spécifie un module de symbole.

 `MODULE_FLAG_64BIT`\
 Spécifie un module 64 bits.

 `MODULE_FLAG_OPTIMIZED`\
 Spécifie que le module a été optimisé. Cet état est reflété dans la fenêtre **modules.**

 `MODULE_FLAG_UNOPTIMIZED`\
 Spécifie que le module n’a pas été optimisé. Cet état est reflété dans la fenêtre **modules.** Il s’agit de la valeur par défaut.

## <a name="remarks"></a>Notes
 Utilisé pour `m_dwModuleFlags` le membre de la structure [MODULE_INFO.](../../../extensibility/debugger/reference/module-info.md)

 Ces drapeaux peuvent être combinés avec un peu plus. `OR`

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
