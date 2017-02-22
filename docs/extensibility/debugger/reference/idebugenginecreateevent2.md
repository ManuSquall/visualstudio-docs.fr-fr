---
title: "IDebugEngineCreateEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineCreateEvent2"
helpviewer_keywords: 
  - "Interface de IDebugEngineCreateEvent2"
ms.assetid: 37c0a841-1c8d-4802-a990-36b54bca3ef7
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugEngineCreateEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Le moteur \(DE\) de débogage envoie cette interface au gestionnaire de débogage de \(SDM\) session lorsqu'une instance De est créée.  
  
## Syntaxe  
  
```  
IDebugEngineCreateEvent2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le De implémente cette interface dans le cadre de ses opérations normales.  L'interface d' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface \(le SDM utilise la méthode de l' `QueryInterface` pour accéder à l'interface d' `IDebugEvent2` \).  
  
## Remarques pour les appelants  
 Le du crée et envoie cet objet événement lorsque le De a été instancié.  L'événement est envoyé à l'aide de la fonction de rappel d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu'elle s'est attachée le programme débogué.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugEngineCreateEvent2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)|Récupère l'objet qui représente le moteur de débogage \(DE\) nouvellement créée.|  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)