---
title: "IDebugSymbolSearchEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolSearchEvent2"
helpviewer_keywords: 
  - "IDebugSymbolSearchEvent2"
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugSymbolSearchEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface est envoyée par le moteur de débogage \(DE\) pour indiquer que les symboles de débogage pour un module en cours de débogage ont été chargés.  
  
## Syntaxe  
  
```  
IDebugSymbolSearchEvent2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le De implémente cette interface pour signaler que les symboles d'un module ont été chargés.  l'interface d' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface.  Le SDM utilise [QueryInterface](/visual-cpp/atl/queryinterface) pour accéder à l'interface d' `IDebugEvent2` .  
  
## Remarques pour les appelants  
 Le du crée et envoie cet objet événement pour signaler que les symboles d'un module ont été chargés.  L'événement est envoyé à l'aide de la fonction de rappel d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu'elle s'est attachée le programme débogué.  
  
## méthodes en commande de Vtable  
 l'interface d' `IDebugSymbolSearchEvent2` expose la méthode suivante.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|Récupère des informations sur les résultats d'une recherche de symboles.|  
  
## Notes  
 Cet événement est envoyé même si les symboles n'ont pas été chargés.  Appeler `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` permet au gestionnaire de cet événement pour déterminer si le module a réellement des symboles.  
  
 Visual Studio utilise en général cet événement pour mettre à jour l'état des symboles chargés dans la fenêtre de **Module** .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)