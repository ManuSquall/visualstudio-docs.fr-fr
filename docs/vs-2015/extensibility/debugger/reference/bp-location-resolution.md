---
title: BP_LOCATION_RESOLUTION | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_LOCATION_RESOLUTION
helpviewer_keywords:
- BP_LOCATION_RESOLUTION structure
ms.assetid: 86ea2c8a-54a3-48e8-83c7-18a515273129
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d24ae48df790e452145e5aa8c67998d55760bb24
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953304"
---
# <a name="bplocationresolution"></a>BP_LOCATION_RESOLUTION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Décrit la résolution d’un point d’arrêt à un emplacement spécifique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
typedef struct _BP_LOCATION_RESOLUTION {   
   IDebugBreakpointResolution2* pResolution;  
} BP_LOCATION_RESOLUTION;  
```  
  
## <a name="members"></a>Membres  
 pResolution  
 Le [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) objet qui détermine le type de point d’arrêt et de ses informations de résolution.  
  
## <a name="remarks"></a>Notes  
 Cette structure est un membre de la [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) structure dans le cadre d’une union.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)
