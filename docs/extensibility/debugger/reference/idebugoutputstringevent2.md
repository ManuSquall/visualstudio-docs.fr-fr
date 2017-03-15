---
title: "IDebugOutputStringEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugOutputStringEvent2"
helpviewer_keywords: 
  - "Interface de IDebugOutputStringEvent2"
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugOutputStringEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface est envoyée par le moteur \(DE\) de débogage au gestionnaire de débogage de session \(SDM\) pour produire une chaîne.  
  
## Syntaxe  
  
```  
IDebugOutputStringEvent2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le De implémente cette interface pour envoyer une chaîne dans la fenêtre de **Sortie** de l'IDE.  l'interface d' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface.  Le SDM utilise [QueryInterface](/visual-cpp/atl/queryinterface) pour accéder à l'interface d' `IDebugEvent2` .  
  
## Remarques pour les appelants  
 Le du crée et envoie cet objet événement pour envoyer une chaîne dans la fenêtre de **Sortie** .  L'événement est envoyé à l'aide de la fonction de rappel d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu'elle est associée au programme en cours de débogage.  
  
## méthodes en commande de Vtable  
 le tableau suivant montre la méthode d' `IDebugOutputStringEvent2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetString](../Topic/IDebugOutputStringEvent2::GetString.md)|Reçoit le message affiché.|  
  
## Notes  
 Par exemple, dans du code non managé, la chaîne à être sortie peut démarrer lorsque le programme débogué envoie une chaîne à la fonction Win32 `OutputDebugString` .  Cette chaîne est arrêtée par le De et en fonction envoyée au SDM comme un événement d' `IDebugOutputStringEvent2` .  
  
 Utilisez [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) pour envoyer un message qui requiert des réponses d'utilisateur.  
  
 Utilisez [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) pour envoyer un message d'erreur qui ne requiert pas de réponse.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)