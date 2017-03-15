---
title: IDebugBoundBreakpoint2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 3406c6b415523ff8ec46b71b649a81a44fb01c66
ms.lasthandoff: 02/22/2017

---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
Cette interface représente un point d’arrêt est lié à un emplacement du code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugBoundBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes relatives à l’attention des implémenteurs  
 Le moteur de débogage (DE) implémente cette interface dans le cadre de sa prise en charge des points d’arrêt.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Un appel à [lier](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) crée cette interface. Les appels à [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) et [suivant](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) peuvent également obtenir cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugBoundBreakpoint2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Obtient le point d’arrêt en attente à partir de laquelle le point d’arrêt lié spécifié a été créé.|  
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Obtient l’état de ce point d’arrêt lié.|  
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Obtient le nombre d’accès actuel pour ce point d’arrêt lié.|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Obtient la résolution de point d’arrêt qui décrit ce point d’arrêt.|  
|[Activer](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Active ou désactive le point d’arrêt.|  
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Définit le nombre d’accès pour ce point d’arrêt lié.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Définit ou modifie la condition associée à ce point d’arrêt lié.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Définit ou modifier le nombre de passe associé à ce point d’arrêt lié.|  
|[Supprimer](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Supprime le point d'arrêt.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)   
 [Suivant](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)   
 [Lier](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
