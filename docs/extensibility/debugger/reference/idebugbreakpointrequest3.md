---
title: "IDebugBreakpointRequest3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointRequest3"
helpviewer_keywords: 
  - "IDebugBreakpointRequest3"
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugBreakpointRequest3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface représente les informations nécessaires pour créer et lier n'importe quel type de point d'arrêt.  Il s'agit d'une extension d' [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).  
  
## Syntaxe  
  
```  
IDebugBreakpointRequest3 : IDebugBreakpointRequest2  
```  
  
## Remarques à l'intention des implémenteurs  
 Le gestionnaire de débogage de session \(SDM\) implémente généralement cette interface.  
  
## Remarques pour les appelants  
 le moteur de débogage \(DE\) accède à cette interface en appelant [QueryInterface](/visual-cpp/atl/queryinterface) sur l'interface IDebugBreakpointRequest2 reçue dans un appel à [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).  
  
## méthodes en commande de Vtable  
 Outre les méthodes héritées de [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md), l'interface `IDebugBreakpointRequest3` expose la méthode suivante.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Obtient les informations de requête de point d'arrêt qui décrivent cette requête de point d'arrêt.|  
  
## Notes  
 Cette interface est utilisée pour fournir des informations supplémentaires au De dans la structure de [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .  Ces informations supplémentaires incluent l'ID du fournisseur De \(sous la forme de GUID\), le nom d'un point de trace, et le nom d'une contrainte de point d'arrêt.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)