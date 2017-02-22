---
title: "IDebugEngineProgram2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineProgram2"
helpviewer_keywords: 
  - "Interface de IDebugEngineProgram2"
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugEngineProgram2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface fournit la prise en charge du débogage multithread.  
  
## Syntaxe  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Un moteur de débogage implémente cette interface pour prendre en charge le débogage simultané plusieurs threads.  cette interface est implémentée sur le même objet qui implémente l'interface d' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) .  
  
## Remarques pour les appelants  
 utilisation [QueryInterface](/visual-cpp/atl/queryinterface) d'obtenir cette interface d'une interface d' `IDebugProgram2` .  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugEngineProgram2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Arrêter](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Arrête tous les threads exécuter dans ce programme.|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|La recherche de l'exécution \(ou l'arrêt recherche de l'exécution\) se produire sur le thread donné.|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Permet \(ou rejette\) à l'évaluation de l'expression pour se produire sur le thread donné, même si le programme est arrêté.|  
  
## Notes  
 Visual Studio appelle cette interface en réponse à un événement d' [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) et pour définir « indique que l'étape de thread » et « explique pour l'évaluation d'une expression les rapports sur thread » du programme.  [Arrêter](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) est appelé lorsque le programme doit être arrêté ; cette méthode permet au programme la possibilité de terminer tous les threads.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)