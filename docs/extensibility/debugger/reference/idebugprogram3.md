---
title: "IDebugProgram3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugProgram3"
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugProgram3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface représente un programme qui s'exécute dans un processus et étend [Exécuter](../../../extensibility/debugger/reference/idebugprogram2-execute.md) en fournissant les informations de thread.  
  
## Syntaxe  
  
```  
IDebugProgram3 : IDebugProgram3  
```  
  
## Remarques à l'intention des implémenteurs  
 Le moteur \(DE\) de débogage et un fournisseur de port implémentent cette interface pour représenter un programme dans un processus.  le gestionnaire de débogage de session \(SDM\) implémente également cette interface pour fournir des informations à [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## Remarques pour les appelants  
 L'événement d' [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) retourne cette interface pour un nouveau programme.  Cette interface est également utilisée comme paramètre pour de nombreuses méthodes sur plusieurs interfaces.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugProgram3`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|exécute le programme.  Le thread est retourné pour fournir au débogueur des informations sur lesquels le thread l'utilisateur s'affiche en exécutant l'.|  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Notes  
 Un programme est un bon fonctionnement de conteneur de thread dans l'architecture à l'exécution particulière, alors qu'un processus contient un ou plusieurs programmes.  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [GetProgram](../Topic/IDebugThread2::GetProgram.md)   
 [Suivant](../Topic/IEnumDebugPrograms2::Next.md)   
 [Événement](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)