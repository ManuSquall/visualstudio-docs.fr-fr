---
title: IDebugModule2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9fc229a353655aeae06460c32b5233888f22dd6e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555808"
---
# <a name="idebugmodule2"></a>IDebugModule2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface représente un module, c’est-à-dire une unité exécutable d’un programme, tel qu’une DLL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugModule2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur DE débogage (DE) implémente cette interface pour représenter un module et pour fournir l’accès aux informations sur ce module.  
  
## <a name="notes-for-callers"></a>Notes pour les appelants  
 Un appel à [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) retourne cette interface. Le DE envoie l’interface [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) au gestionnaire de débogage de session (SDM) à l’aide de la méthode d' [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) .  
  
 Cette interface peut également être retournée dans une structure [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) (qui est retournée par un appel à [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)).  
  
 [Next](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) retourne également cette interface ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) retourne l’interface [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) ).  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugModule2` .  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Obtient le [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) qui décrit ce module.|  
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|OBSOLÈTE. N’UTILISEZ PAS. Recharge les symboles pour ce module.|  
  
## <a name="remarks"></a>Notes  
 Les informations de module peuvent être affichées dans la fenêtre **modules** de l’IDE.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
