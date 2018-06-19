---
title: IDebugFunctionPosition2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 73097a7133de095d72a6ae22b9aff701b52ef191
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31112527"
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
Cette interface représente une position abstraite d’une fonction dans un document source.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugFunctionPosition2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur de débogage (DE) implémente cette interface pour représenter la position d’une fonction dans un document source.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Cette interface est fournie en tant que partie d’un [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) union (plus précisément, un [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) structure) qui est à son tour partie de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) structure, utilisée pour la création d’un point d’arrêt en attente.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugFunctionPosition2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Obtient le nom de la fonction relatif à cette position.|  
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|Obtient le décalage à partir du début de la fonction.|  
  
## <a name="remarks"></a>Notes  
 La position représentée par cette interface est basé sur le texte, en particulier, un [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) structure.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)