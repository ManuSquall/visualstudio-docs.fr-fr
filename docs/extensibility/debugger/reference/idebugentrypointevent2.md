---
title: "IDebugEntryPointEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEntryPointEvent2"
helpviewer_keywords: 
  - "Interface de IDebugEntryPointEvent2"
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugEntryPointEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Le moteur \(DE\) de débogage envoie cette interface au gestionnaire de débogage de session \(SDM\) lorsque le programme est sur le point d'exécution de sa première instruction de code utilisateur.  
  
## Syntaxe  
  
```  
IDebugEntryPointEvent2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le De implémente cette interface dans le cadre de ses opérations normales.  l'interface d' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface.  Le SDM utilise [QueryInterface](/visual-cpp/atl/queryinterface) pour accéder à l'interface d' `IDebugEvent2` .  
  
## Remarques pour les appelants  
 Le du crée et envoie cet objet événement lorsque le programme débogué a été chargé et est prêt à exécuter la première instruction de code utilisateur.  L'événement est envoyé à l'aide de la fonction de rappel d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu'elle s'est attachée le programme débogué.  
  
## Notes  
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) est envoyé lorsque le programme est sur le point d'exécuter la toute première instruction.  Par exemple, `IDebugEntryPoint2` est envoyé lorsque le programme est sur le point d'exécuter la fonction d' `main` de l'utilisateur.  
  
 Lorsque le De envoie `IDebugEntryPointEvent2`, la position du code en cours doit être à la première instruction de code utilisateur, comme `main`.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)