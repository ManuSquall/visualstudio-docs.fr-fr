---
title: BP_LOCATION_CODE_FUNC_OFFSET | Microsoft Docs
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
- BP_LOCATION_CODE_FUNC_OFFSET
helpviewer_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET structure
ms.assetid: ab38f7ca-fa01-4cf3-a06c-56cbb7207617
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b68f01e73703e16aba6daf05df449c17a2662c14
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495499"
---
# <a name="bplocationcodefuncoffset"></a>BP_LOCATION_CODE_FUNC_OFFSET
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [BP_LOCATION_CODE_FUNC_OFFSET](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/bp-location-code-func-offset).  
  
Décrit l’emplacement de décalage d’un point d’arrêt dans une fonction dans le code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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

