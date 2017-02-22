---
title: "IDebugErrorBreakpoint2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugErrorBreakpoint2"
helpviewer_keywords: 
  - "Interface de IDebugErrorBreakpoint2"
ms.assetid: 1f2a4b94-3713-46e9-8272-3917187792bd
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugErrorBreakpoint2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface représente une erreur ou un point d'arrêt d'avertissement, tel qu'un emplacement valide, une expression valide, ou les raisons pour lesquelles le point d'arrêt en attente n'a pas lié \(code non chargé encore, etc.\).  
  
## Syntaxe  
  
```  
IDebugErrorBreakpoint2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Un moteur de débogage implémente cette interface dans le cadre de son prise en charge des points d'arrêt.  cette interface est utilisée pour signaler des problèmes avec lier un point d'arrêt.  
  
## Remarques pour les appelants  
 Un appel à [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) reçoit cette interface.  Cette interface peut également être retournée \(dans le cadre d'une liste représentée par une interface d' [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md) \) par un appel à [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) ou à [EnumErrorBreakpoints](../Topic/IDebugPendingBreakpoint2::EnumErrorBreakpoints.md).  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugErrorBreakpoint2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|obtient le point d'arrêt en attente qui a provoqué l'erreur.|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|obtient la résolution d'erreur de point d'arrêt qui décrit l'erreur.|  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)   
 [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)   
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)   
 [Suivant](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)