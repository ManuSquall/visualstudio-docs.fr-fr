---
title: IDebugBoundBreakpoint2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ad36363ff20e285dde2db6fc723ddf2562c491f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156164"
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface représente un point d’arrêt qui est lié à un emplacement de code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugBoundBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur de débogage (DE) implémente cette interface dans le cadre de sa prise en charge des points d’arrêt.  
  
## <a name="notes-for-callers"></a>Notes pour les appelants  
 Un appel à [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) crée cette interface. Les appels à [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) et [Next](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) peuvent également obtenir cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugBoundBreakpoint2` .  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Obtient le point d’arrêt en attente à partir duquel le point d’arrêt lié spécifié a été créé.|  
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Obtient l’état de ce point d’arrêt lié.|  
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Obtient le nombre d’accès actuel pour ce point d’arrêt lié.|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Obtient la résolution de point d’arrêt qui décrit ce point d’arrêt.|  
|[Activer](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Active ou désactive le point d’arrêt.|  
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Définit le nombre d’accès pour ce point d’arrêt lié.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Définit ou modifie la condition associée à ce point d’arrêt lié.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Définit ou modifie le nombre de tests associés à ce point d’arrêt lié.|  
|[Supprimer](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Supprime le point d'arrêt.|  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)   
 [Situé](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)   
 [Établis](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
