---
title: "IDebugErrorBreakpointResolution2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugErrorBreakpointResolution2"
helpviewer_keywords: 
  - "IDebugErrorBreakpointResolution2"
ms.assetid: b1234216-0ac8-461d-b2a7-54f60f8f3262
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugErrorBreakpointResolution2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface représente la résolution d'une erreur de point d'arrêt.  
  
## Syntaxe  
  
```  
IDebugErrorBreakpointResolution2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Un moteur de débogage implémente cette interface dans le cadre de son prise en charge des points d'arrêt.  Cette interface est utilisée pour stocker où un point d'arrêt n'a pas lié.  
  
## Remarques pour les appelants  
 Un appel à [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) retourne cette interface pour fournir des informations concernant l'emplacement où le point d'arrêt n'a pas lié.  la méthode d' [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) obtient l'interface d' [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) .  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugErrorBreakpointResolution2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|obtient le type de point d'arrêt.|  
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|obtient les informations sur la résolution de point d'arrêt.|  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)   
 [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)