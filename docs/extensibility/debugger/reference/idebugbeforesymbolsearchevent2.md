---
title: "IDebugBeforeSymbolSearchEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugBeforeSymbolSearchEvent2"
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugBeforeSymbolSearchEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Le moteur \(DE\) de débogage envoie cette interface au gestionnaire de débogage de session \(SDM\) pour définir le message de barre d'état pendant le chargement du symbole.  
  
## Syntaxe  
  
```  
IDebugBeforeSymbolSearchEvent2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le De implémente cette interface lorsqu'il doit définir le message de barre d'état pendant le chargement du symbole.  Cette interface est implémentée uniquement par les moteurs de débogage qui fonctionnent avec ou est une partie d'interpréteurs de scripts.  L'interface d' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface \(le SDM utilise **QueryInterface** pour accéder à l'interface **IDebugEvent2** \).  
  
## Remarques pour les appelants  
 Le du crée et envoie cet objet événement lorsqu'il doit définir le message de barre d'état pendant le chargement du symbole.  L'événement est envoyé à l'aide de la fonction de rappel d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu'il est attaché au programme en cours de débogage.  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes d' `IDebugBeforeSymbolSearchEvent2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Extrait le nom du module actuellement en cours de débogage.|  
  
## Configuration requise  
 en\-tête : Msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll