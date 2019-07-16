---
title: REFERENCE_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- REFERENCE_TYPE
helpviewer_keywords:
- REFERENCE_TYPE enumeration
ms.assetid: b1ffba10-eb9d-48ba-bf48-6d8b71d6f270
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 509c0bc4547ca057c39a6c07ba8ccbe63743b914
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204906"
---
# <a name="referencetype"></a>REFERENCE_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Spécifie le type de référence.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum enum_REFERENCE_TYPE {   
   REF_TYPE_WEAK   = 0x0001,  
   REF_TYPE_STRONG = 0x0002  
};  
typedef DWORD REFERENCE_TYPE;  
```  
  
```csharp  
public enum enum_REFERENCE_TYPE {   
   REF_TYPE_WEAK   = 0x0001,  
   REF_TYPE_STRONG = 0x0002  
};  
```  
  
## <a name="members"></a>Membres  
 REF_TYPE_WEAK  
 Spécifie une référence faible. Ne peut pas être combiné avec `REF_TYPE_STRONG`.  
  
 REF_TYPE_STRONG  
 Spécifie une référence forte. Ne peut pas être combiné avec `REF_TYPE_WEAK`.  
  
## <a name="remarks"></a>Notes  
 Utilisé en tant que le `dwRefType` membre de la [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) structure.  
  
 Passé en tant que paramètre à la [SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md) (méthode).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)
