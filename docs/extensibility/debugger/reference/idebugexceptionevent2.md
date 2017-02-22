---
title: "IDebugExceptionEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExceptionEvent2"
helpviewer_keywords: 
  - "Interface de IDebugExceptionEvent2"
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExceptionEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Le moteur \(DE\) de débogage envoie cette interface au gestionnaire de débogage de session \(SDM\) lorsqu'une exception est levée dans le programme actuellement en cours de exécution.  
  
## Syntaxe  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le De implémente cette interface pour signaler qu'une exception s'est produite dans le programme débogué.  l'interface d' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface.  Le SDM utilise [QueryInterface](/visual-cpp/atl/queryinterface) pour accéder à l'interface d' `IDebugEvent2` .  
  
## Remarques pour les appelants  
 Le du crée et envoie cet objet événement pour enregistrer une exception.  L'événement est envoyé à l'aide de la fonction de rappel d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu'elle s'est attachée le programme débogué.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugExceptionEvent2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetException](../Topic/IDebugExceptionEvent2::GetException.md)|Obtient les informations détaillées sur l'exception qui a déclenché l'événement.|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Obtient une description explicite pour l'exception levée qui a déclenché l'événement.|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Détermine si le moteur de \(DE\) débogage prennent en charge l'option de passer cette exception au programme en cours de débogage lorsque l'exécution se poursuit.|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Spécifie si l'exception doit être passée dans le programme débogué lorsque l'exécution se poursuit, ou si l'exception est ignorée.|  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Notes  
 Avant d'envoyer l'événement, le De vérifie si cet événement exception a été lu une première chance ou une exception de seconde chance par un appel précédent à [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md).  S'il était indiqué pour être une exception de première chance, l'événement d' `IDebugExceptionEvent2` est envoyé au SDM.  Sinon, le De donne à l'application la possibilité de gérer l'exception.  Si aucun gestionnaire d'exceptions n'est fourni, et si l'exception a été indiquée comme une exception de seconde chance, l'événement d' `IDebugExceptionEvent2` est envoyé au SDM.  Sinon, le De reprend l'exécution du programme, et le système d'exploitation ou le runtime gère l'exception.  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)