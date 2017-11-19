---
title: IDebugModule2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModule2
helpviewer_keywords: IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dd8600c592993d24d07add88425e534d5ae99867
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmodule2"></a>IDebugModule2
Cette interface représente un module, autrement dit, une unité exécutable d’un programme, par exemple une DLL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugModule2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur de débogage (DE) implémente cette interface pour représenter un module et pour fournir l’accès aux informations relatives à ce module.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Un appel à [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) retourne cette interface. L’envoie DE la [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) de l’interface pour le Gestionnaire de débogage de session (SDM) à l’aide de la [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) (méthode).  
  
 Cette interface peut également être renvoyée dans un [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) structure (qui est retournée par un appel à [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)).  
  
 [Suivant](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) retourne également cette interface ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) retourne le [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) interface).  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugModule2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Obtient le [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) qui décrit ce module.|  
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|OBSOLÈTE. N’UTILISEZ PAS. Recharge les symboles de ce module.|  
  
## <a name="remarks"></a>Remarques  
 Informations du module peuvent être affichées dans le **Modules** fenêtre de l’IDE.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)