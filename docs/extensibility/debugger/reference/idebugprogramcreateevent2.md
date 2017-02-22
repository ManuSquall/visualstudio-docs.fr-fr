---
title: "IDebugProgramCreateEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramCreateEvent2"
helpviewer_keywords: 
  - "Interface de IDebugProgramCreateEvent2"
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProgramCreateEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface est envoyée par le moteur \(DE\) de débogage au gestionnaire de débogage de \(SDM\) session lorsqu'un programme est attaché.  
  
## Syntaxe  
  
```  
IDebugProgramCreateEvent2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le De ou le fournisseur de port implémente cette interface pour signaler qu'un programme a été créé, généralement lorsque le programme est attaché.  l'interface d' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface.  Le SDM utilise la méthode de l' `QueryInterface` pour accéder à l'interface d' `IDebugEvent2` .  
  
## Remarques pour les appelants  
 Le De ou le fournisseur de port crée et envoie cet objet événement pour signaler la création d'un programme.  Le De envoie cet événement à l'aide de la fonction de rappel d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu'elle s'est attachée le programme débogué.  Le fournisseur de port envoie cet événement à l'aide de l'interface d' [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) .  
  
## Notes  
 Le De ou le fournisseur de port émet une nouvelle interface d' [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) en appelant [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)