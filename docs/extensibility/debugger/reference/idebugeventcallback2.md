---
title: "IDebugEventCallback2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEventCallback2"
helpviewer_keywords: 
  - "IDebugEventCallback2"
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugEventCallback2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface est utilisée par le moteur \(DE\) de débogage pour envoyer des événements de débogage au gestionnaire de débogage de session \(SDM\).  
  
## Syntaxe  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] implémente cette interface pour recevoir des événements d'un moteur de débogage.  
  
## Remarques pour les appelants  
 Un moteur de débogage accepte généralement cette interface lorsque le SDM appelle [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md), ou [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  un moteur de débogage envoie des événements au SDM en appelant [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugEventCallback2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Envoie des notifications d'événement de débogage au SDM.|  
  
## Notes  
 bien qu' [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) et [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) spécifient qu'ils prennent une interface d' `IDebugEventCallback2` , ce n'est pas le cas, et le pointeur d'interface sera toujours une valeur NULL.  À la place, le moteur de débogage doit utiliser l'interface d' `IDebugEventCallback2` reçue dans l'appel à [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), à [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md), ou à [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Si un package implémente [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) en code managé, on fortement recommandé qu' <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> soit appelé sur les différentes interfaces qui sont passées à [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)