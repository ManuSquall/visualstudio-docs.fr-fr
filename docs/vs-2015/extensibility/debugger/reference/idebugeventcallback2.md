---
title: IDebugEventCallback2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5517050ffba73ae495300a5d32d40fd8dbc7c57c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49226250"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface est utilisée par le moteur de débogage (dé) pour envoyer des événements de débogage pour le Gestionnaire de session de débogage (SDM).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] implémente cette interface pour recevoir des événements à partir d’un moteur de débogage.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Un moteur de débogage reçoit généralement cette interface lorsque le SDM appelle [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md), ou [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Un moteur de débogage envoie des événements pour le SDM en appelant [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugEventCallback2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Envoie une notification de débogage des événements pour le SDM.|  
  
## <a name="remarks"></a>Notes  
 Bien que [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) et [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) spécifier qu’ils prennent une `IDebugEventCallback2` interface, cela n’est pas le cas, et le pointeur d’interface sera toujours une valeur null. Au lieu de cela, le moteur de débogage doit utiliser le `IDebugEventCallback2` reçus dans l’appel à interface [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md), ou [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Si un package implémente [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) en code managé, il est fortement recommandé que <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> appelée sur les diverses interfaces qui sont passées à [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attacher](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)

