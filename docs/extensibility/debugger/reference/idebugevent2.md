---
title: "IDebugEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEvent2"
helpviewer_keywords: 
  - "Interface de IDebugEvent2"
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface est utilisée pour transmettre les informations de débogage critiques, telles que l'arrêt à un point d'arrêt, et aux informations non critiques, telles qu'un message de débogage.  
  
## Syntaxe  
  
```  
IDebugEvent2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le moteur \(DE\) de débogage et le fournisseur de port implémentent cette interface sur le même objet que toutes les autres interfaces d'événement.  
  
## Remarques pour les appelants  
 À l'aide de l'argument de l'ID d'interface \(IID\) donné à [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ou à [Événement](../../../extensibility/debugger/reference/idebugportevents2-event.md), les appels [QueryInterface](/visual-cpp/atl/queryinterface) de gestionnaire \(SDM\) de débogage de session à l'interface d' `IDebugEvent2` pour obtenir l'interface d'événement appropriée.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugEvent2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Obtient les attributs de cet événement de débogage.|  
  
## Notes  
 Les interfaces d'événement plus spécifiques, telles que [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), ne dérivent pas de l'interface IDebugEvent2 mais sont plutôt implémentées comme une interface distincte sur le même objet qu' `IDebugEvent2`.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Événement](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)