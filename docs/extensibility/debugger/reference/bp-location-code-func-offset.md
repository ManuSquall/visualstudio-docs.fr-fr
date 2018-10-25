---
title: BP_LOCATION_CODE_FUNC_OFFSET | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET
helpviewer_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET structure
ms.assetid: ab38f7ca-fa01-4cf3-a06c-56cbb7207617
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9a1828a7cea62893ecddec6d28f44ca6475352dd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911393"
---
# <a name="bplocationcodefuncoffset"></a>BP_LOCATION_CODE_FUNC_OFFSET
Décrit l’emplacement de décalage d’un point d’arrêt dans une fonction dans le code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _BP_LOCATION_CODE_FUNC_OFFSET {   
   BSTR                     bstrContext;  
   IDebugFunctionPosition2* pFuncPos;  
} BP_LOCATION_CODE_FUNC_OFFSET;  
```  
  
## <a name="members"></a>Membres  
 `bstrContext`  
 Le contexte du point d’arrêt, généralement un nom de méthode ou fonction tels que présentés sur une pile des appels.  
  
 `pFuncPos`  
 Le [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md) objet qui décrit le nom de la fonction et la position relative à partir du début de la fonction.  
  
## <a name="remarks"></a>Notes  
 Cette structure est un membre de la [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) structure dans le cadre d’une union.  
  
 Le `pFuncPos` membre indique où définir le point d’arrêt de la fonction.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)