---
title: MODULE_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 224a6db4b6c4860a2bf9a0b326319a3be1efc6a6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494838"
---
# <a name="moduleflags"></a>MODULE_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [MODULE_FLAGS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/module-flags).  
  
Utilisé pour décrire un module.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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

