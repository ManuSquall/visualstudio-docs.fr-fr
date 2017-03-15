---
title: "IDebugInterceptExceptionCompleteEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugInterceptExceptionCompleteEvent2"
helpviewer_keywords: 
  - "IDebugInterceptExceptionCompleteEvent2"
ms.assetid: 8ebc256b-5428-4ed6-a505-6aedc8242b8e
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugInterceptExceptionCompleteEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface est envoyée par le moteur \(DE\) de débogage au gestionnaire de débogage de session \(SDM\) lorsque le De a terminé la gestion d'un événement désactivé.  
  
## Syntaxe  
  
```  
IDebugInterceptExceptionCompleteEvent2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le De implémente cette interface pour signaler que le traitement d'une exception interceptée a été effectué.  l'interface d' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface.  Le SDM utilise [QueryInterface](/visual-cpp/atl/queryinterface) pour accéder à l'interface d' `IDebugEvent2` .  
  
## Remarques pour les appelants  
 Le du crée et envoie cet objet événement pour signaler l'achèvement d'une exception arrête.  L'événement est envoyé à l'aide de la fonction de rappel d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu'elle s'est attachée le programme débogué.  
  
## méthodes en commande de Vtable  
 L'interface d' `IDebugInterceptExceptionCompleteEvent2` implémente les méthodes suivantes.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetInterceptCookie](../Topic/IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie.md)|Retourne la valeur unique associée à l'exception gérée.|  
  
## Notes  
 Cet événement est envoyé par [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) lorsque cette méthode a terminé avec succès gérer une exception arrête.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)