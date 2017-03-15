---
title: "IDebugBreakEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakEvent2"
helpviewer_keywords: 
  - "Interface de IDebugBreakEvent2"
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugBreakEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface indique au gestionnaire de débogage de session \(SDM\) qu'un saut asynchrone a été effectué avec succès.  
  
## Syntaxe  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le De implémente cette interface pour prendre en charge des sauts d'utilisateur dans un programme.  L'interface d' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface \(le SDM utilise [QueryInterface](/visual-cpp/atl/queryinterface) pour accéder à l'interface d' `IDebugEvent2` \).  
  
## Remarques pour les appelants  
 Le SDM appelle [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) lorsque l'utilisateur a demandé le programme débogué pour être interrompu.  Lorsque le programme a été correctement suspendu, le De envoie l'événement d' `IDebugBreakEvent2` .  Cet événement est envoyé à l'aide de la fonction de rappel d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu'il est attaché au programme en cours de débogage.  
  
## Notes  
 Par exemple, un utilisateur peut sélectionner la commande d' **Interrompre tout** dans le menu de **Débogage** de quitter d'un programme s'exécutant une boucle infinie.  Le SDM indique au programme arrêter en appelant [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md).  Le De envoie `IDebugBreakEvent2` lorsque le programme s'arrête finally.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)