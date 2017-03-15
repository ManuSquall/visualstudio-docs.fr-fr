---
title: "IDebugPropertyCreateEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPropertyCreateEvent2"
helpviewer_keywords: 
  - "Interface de IDebugPropertyCreateEvent2"
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugPropertyCreateEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface est envoyée par le moteur \(DE\) de débogage au gestionnaire de débogage de \(SDM\) session lorsqu'il crée une propriété qui est associée à un document spécifique.  
  
## Syntaxe  
  
```  
IDebugPropertyCreateEvent2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le De implémente cette interface pour signaler qu'une propriété a été créée.  l'interface d' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface.  Le SDM utilise [QueryInterface](/visual-cpp/atl/queryinterface) pour accéder à l'interface d' `IDebugEvent2` .  Cette interface est implémentée si le De a créé une propriété associée à un script qui a été chargé ou créé et que ce script doit apparaître dans l'IDE.  
  
## Remarques pour les appelants  
 Le du crée et envoie cet objet événement pour signaler qu'une propriété a été créée.  L'événement est envoyé à l'aide de la fonction de rappel d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu'elle est associée au programme en cours de débogage.  
  
## méthodes en commande de Vtable  
 le tableau suivant montre la méthode d'interface d' `IDebugPropertyCreateEvent2` .  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|obtient la nouvelle propriété.|  
  
## Notes  
 Si une propriété possède un document spécifique ou un script qui lui est associé, le De peut envoyer cet événement au SDM pour mettre à jour la fenêtre de **documents de script** avec le nom du document.  Le SDM appelle [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) avec l'argument `guidDocument` pour récupérer `VARIANT` contenant un pointeur d' [IUnknown](/visual-cpp/atl/iunknown) .  Le SDM appelle [QueryInterface](/visual-cpp/atl/queryinterface) sur ce pointeur pour récupérer l'interface d' [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) utilisée pour mettre à jour la fenêtre de **documents de script** .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)