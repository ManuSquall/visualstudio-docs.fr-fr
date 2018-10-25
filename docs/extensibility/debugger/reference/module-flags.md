---
title: MODULE_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 89dbb562dfbab83f56664aad7fdd107ea9d0e397
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873972"
---
# <a name="moduleflags"></a>MODULE_FLAGS
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
  
## <a name="members"></a>Membres  
 MODULE_FLAG_NONE  
 Ne spécifie aucun module.  
  
 MODULE_FLAG_SYSTEM  
 Spécifie un module de système.  
  
 MODULE_FLAG_SYMBOLS  
 Spécifie un module de symbole.  
  
 MODULE_FLAG_64BIT  
 Spécifie un module 64 bits.  
  
 MODULE_FLAG_OPTIMIZED  
 Spécifie que le module a été optimisé. Cet état est reflété dans le **Modules** fenêtre.  
  
 MODULE_FLAG_UNOPTIMIZED  
 Spécifie que le module n’a pas été optimisé. Cet état est reflété dans le **Modules** fenêtre. Il s’agit de l’état par défaut.  
  
## <a name="remarks"></a>Notes  
 Utilisé pour le `m_dwModuleFlags` membre de la [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) structure.  
  
 Ces indicateurs peuvent être combinées avec un opérateur de bits `OR`.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)