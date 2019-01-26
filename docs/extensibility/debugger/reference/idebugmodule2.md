---
title: IDebugModule2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ea20dac16cdffbac24cbca68c1a337a250ea8cc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922767"
---
# <a name="idebugmodule2"></a>IDebugModule2
Cette interface représente un module, autrement dit, une unité exécutable d’un programme, comme une DLL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugModule2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Le moteur de débogage (dé) implémente cette interface pour représenter un module et pour fournir l’accès aux informations sur ce module.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Un appel à [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) retourne cette interface. L’envoie DE la [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) interface avec le Gestionnaire de débogage de session (SDM) à l’aide de la [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) (méthode).  
  
 Cette interface peut également être retournée dans un [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) structure (qui est retourné par un appel à [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)).  
  
 [Suivant](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) retourne également cette interface ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) retourne le [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) interface).  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugModule2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Obtient le [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) qui décrit ce module.|  
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|OBSOLÈTE. N’UTILISEZ PAS. Recharge les symboles pour ce module.|  
  
## <a name="remarks"></a>Notes  
 Informations de module peuvent être affichées dans le **Modules** fenêtre de l’IDE.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)