---
title: MODULE_INFO_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MODULE_INFO_FLAGS
helpviewer_keywords:
- MODULE_INFO_FLAGS enumeration
ms.assetid: e22d3723-b4d4-4524-8a2f-3adb55bbd273
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 14c9f36c82445f5279615591d38b110163a0829d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953330"
---
# <a name="moduleinfoflags"></a>MODULE_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Spécifie l’état de symboles pour un module.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum enum_MODULE_INFO_FLAGS {  
   MIF_SYMBOLS_LOADED = 0x0001  
};  
typedef DWORD MODULE_INFO_FLAGS;  
```  
  
```csharp  
public enum enum_MODULE_INFO_FLAGS {  
   MIF_SYMBOLS_LOADED = 0x0001  
};  
```  
  
## <a name="members"></a>Membres  
 MIF_SYMBOLS_LOADED  
 Au moins un jeu de symboles a été chargé par le module (sinon aucun symbole n’a été chargé).  
  
## <a name="remarks"></a>Notes  
 Cette valeur est retournée par la [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) (méthode).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
