---
title: "IDebugPropertyDestroyEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPropertyDestroyEvent2"
helpviewer_keywords: 
  - "Interface de IDebugPropertyDestroyEvent2"
ms.assetid: 301b7a75-ecfa-46f1-9131-66cf3e4be147
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugPropertyDestroyEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface est envoyée par le moteur de \(DE\) débogage au gestionnaire de débogage de session \(SDM\) lorsqu'une propriété qui est associée à un document spécifique est sur le point d'être détruite.  
  
## Syntaxe  
  
```  
IDebugPropertyDestroyEvent2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le De implémente cette interface pour signaler qu'une propriété a été détruite.  l'interface d' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface.  Le SDM utilise [QueryInterface](/visual-cpp/atl/queryinterface) pour accéder à l'interface d' `IDebugEvent2` .  Cette interface est implémentée si le De précédemment créé une propriété associée à un script ; détruire la propriété supprime le script associé de l'IDE.  
  
## Remarques pour les appelants  
 Le du crée et envoie cet objet événement pour signaler qu'une propriété a été détruite.  L'événement est envoyé à l'aide de la fonction de rappel d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu'elle est associée au programme en cours de débogage.  
  
## méthodes en commande de Vtable  
 le tableau suivant montre la méthode d' `IDebugPropertyDestroyEvent2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertydestroyevent2-getdebugproperty.md)|Obtient la propriété soit détruit.|  
  
## Notes  
 Consultez les remarques de [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) pour plus d'informations sur la raison ces événements sont utilisés.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)