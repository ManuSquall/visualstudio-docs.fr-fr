---
title: "IDebugCanStopEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCanStopEvent2"
helpviewer_keywords: 
  - "Interface de IDebugBreakpointRequest2"
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugCanStopEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface est utilisée pour indiquer au gestionnaire de débogage de \(SDM\) session s'arrêter à l'emplacement actuel du code.  
  
## Syntaxe  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le moteur de \(DE\) débogage implémente cette interface pour prendre en charge la progression au code source.  L'interface d' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface \(le SDM utilise [QueryInterface](/visual-cpp/atl/queryinterface) pour accéder à l'interface d' `IDebugEvent2` \).  
  
 l'implémentation de cette interface doit communiquer l'appel du SDM d' [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) au moteur de débogage.  Par exemple, vous pouvez le faire avec un message publié sur le thread de gestion des messages du moteur de débogage ou l'objet qui implémente cette interface peut contenir une référence au moteur de débogage et à l'appel au moteur de débogage avec l'indicateur passée dans `IDebugCanStopEvent2::CanStop`.  
  
## Remarques pour les appelants  
 Le De peut envoyer cette méthode chaque fois que le du est pour reprendre l'exécution et De parcourt code.  Cet événement est envoyé à l'aide de la fonction de rappel d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu'il est attaché au programme en cours de débogage.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugCanStopEvent2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetReason](../Topic/IDebugCanStopEvent2::GetReason.md)|obtient la raison pour cet événement.|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Spécifie si le programme débogué doit arrêter à l'emplacement de cet événement \(et envoyer un événement qui décrit la raison pour arrêter\) ou simplement continuer l'exécution.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|obtient le contexte de document qui décrit l'emplacement de cet événement.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|obtient le contexte de code qui décrit l'emplacement de cet événement.|  
  
## Notes  
 Le De envoie cette interface si l'utilisateur effectue un pas \- à \- pas détaillé dans une fonction et De ne trouve pas d'informations de débogage là ou les informations de débogage existent mais le De ne sait pas si le code source peut être affiché pour cet emplacement.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)