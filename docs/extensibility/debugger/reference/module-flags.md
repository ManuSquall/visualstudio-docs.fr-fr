---
title: MODULE_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 41201194ee76f92b4faa101c4811c35b44a0d890
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961883"
---
# <a name="module_flags"></a>MODULE_FLAGS
Utilisé pour décrire un module.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_MODULE_FLAGS { 
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
public enum enum_MODULE_FLAGS { 
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
 Ne spécifie aucun module.

 `MODULE_FLAG_SYSTEM`\
 Spécifie un module système.

 `MODULE_FLAG_SYMBOLS`\
 Spécifie un module de symboles.

 `MODULE_FLAG_64BIT`\
 Spécifie un module 64 bits.

 `MODULE_FLAG_OPTIMIZED`\
 Spécifie que le module a été optimisé. Cet État est reflété dans la fenêtre **modules** .

 `MODULE_FLAG_UNOPTIMIZED`\
 Spécifie que le module n’a pas été optimisé. Cet État est reflété dans la fenêtre **modules** . Il s’agit de la valeur par défaut.

## <a name="remarks"></a>Notes
 Utilisé pour le `m_dwModuleFlags` membre de la structure [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) .

 Ces indicateurs peuvent être combinés avec une opération au niveau du bit `OR` .

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
