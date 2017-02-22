---
title: "IDebugBreakpointRequest2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointRequest2"
helpviewer_keywords: 
  - "Interface de IDebugBreakpointRequest2"
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugBreakpointRequest2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface représente les informations nécessaires pour créer et lier n'importe quel type de point d'arrêt.  
  
## Syntaxe  
  
```  
IDebugBreakpointRequest2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le gestionnaire de débogage de session \(SDM\) implémente généralement cette interface.  
  
## Remarques pour les appelants  
 Le moteur \(DE\) de débogage reçoit cette interface via un appel à [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) pour créer un point d'arrêt en attente.  Un appel à [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) peut récupérer cette interface du De.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugBreakpointRequest2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Obtient le type d'emplacement du point d'arrêt sur cette requête de point d'arrêt.|  
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Obtient les informations de requête de point d'arrêt qui décrivent cette requête de point d'arrêt.|  
  
## Notes  
 Une fois le programme débogué chargé, un appel à [Lier](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) lie un point d'arrêt en attente à l'emplacement demandé dans le programme.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)   
 [Lier](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)