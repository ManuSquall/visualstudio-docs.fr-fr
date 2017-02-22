---
title: "IDebugBreakpointEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointEvent2"
helpviewer_keywords: 
  - "Interface de IDebugBreakpointEvent2"
ms.assetid: 50b3a7a7-331b-42c8-922c-ff3522ebe1da
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugBreakpointEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Le moteur \(DE\) de débogage envoie cette interface au gestionnaire de débogage de session \(SDM\) lorsqu'un programme s'arrête à un point d'arrêt.  
  
## Syntaxe  
  
```  
IDebugBreakpointEvent2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le De implémente cette interface dans le cadre de son prise en charge des points d'arrêt.  L'interface d' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface \(le SDM utilise [QueryInterface](/visual-cpp/atl/queryinterface) pour accéder à l'interface d' `IDebugEvent2` \).  
  
## Remarques pour les appelants  
 Le du crée et envoie cet objet événement lorsqu'au moins un point d'arrêt est produit dans le programme.  L'événement est envoyé à l'aide de la fonction de rappel d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu'il est attaché au programme en cours de débogage.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugBreakpointEvent2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)|Crée un énumérateur pour tous les points d'arrêt qui les a déclenché à l'emplacement actuel du code.|  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)