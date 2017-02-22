---
title: "IDebugPortEvents2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEvents2"
helpviewer_keywords: 
  - "Interface de IDebugPortEvents2"
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# IDebugPortEvents2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface signale à un écouteur \(en général le gestionnaire de débogage de session \[SDM\] ou un moteur de débogage\) de processus et création et la destruction de programme sur un port spécifique.  Ces informations peuvent être utilisées pour présenter une vue en temps réel des processus et des programmes à s'exécuter sur le port.  
  
## Syntaxe  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Visual Studio implémente généralement cette interface pour recevoir des notifications sur la création et la destruction du programme.  Un moteur de débogage peut également implémenter cette interface pour écouter des événements de ce type de port.  
  
## Remarques pour les appelants  
 toutes les interfaces d' [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) peuvent être interrogées pour une interface d' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> .  La méthode d' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> pour `IDebugPortEvents2` est appelée dans l'interface d' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> pour obtenir une interface d' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> .  Enfin, la méthode d' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> dans l'interface d' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> est appelée pour envoyer des événements via la méthode d' [Événement](../../../extensibility/debugger/reference/idebugportevents2-event.md) .  
  
## méthodes en commande de Vtable  
 le tableau suivant montre la méthode d' `IDebugPortEvents2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Événement](../../../extensibility/debugger/reference/idebugportevents2-event.md)|envoie les événements qui décrivent la création et la destruction des processus et des programmes sur le port.|  
  
## Notes  
 `IDebugPortEvents2` est également utilisé par le SDM aux programmes de débogage qui fonctionnent dans un processus qui déjà est débogué.  
  
 Les événements de port sont passés au SDM par cette interface.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)