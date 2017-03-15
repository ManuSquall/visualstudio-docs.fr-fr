---
title: "IDebugProgramDestroyEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramDestroyEvent2"
helpviewer_keywords: 
  - "IDebugProgramDestroyEvent2"
ms.assetid: ddf127ca-c4a5-4071-90ca-68faf2f57dbd
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgramDestroyEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface est envoyée par le \(DE\) moteur de débogage au gestionnaire de débogage de \(SDM\) session lorsqu'un programme est terminée.  
  
## Syntaxe  
  
```  
IDebugProgramDestroyEvent2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le De ou le fournisseur de port implémente cette interface pour signaler qu'un programme se termine et n'est plus disponible pour le débogage.  l'interface d' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface.  Le SDM utilise [QueryInterface](/visual-cpp/atl/queryinterface) pour accéder à l'interface d' `IDebugEvent2` .  
  
## Remarques pour les appelants  
 Le De ou le fournisseur de port crée et envoie cet objet événement pour signaler l'arrêt d'un programme.  Le De envoie cet événement à l'aide de la fonction de rappel d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu'elle s'est attachée le programme débogué.  Le fournisseur de port envoie cet événement à l'aide de l'interface d' [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) .  
  
## méthodes en commande de Vtable  
 le tableau suivant montre la méthode d' `IDebugProgramDestroyEvent2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetExitCode](../Topic/IDebugProgramDestroyEvent2::GetExitCode.md)|Obtient le code de sortie du programme.|  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)