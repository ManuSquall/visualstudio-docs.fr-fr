---
title: "IEnumDebugThreads2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugThreads2"
helpviewer_keywords: 
  - "IEnumDebugThreads2"
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugThreads2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cet interfac énumère les threads qui s'exécutent dans la session de débogage en cours.  
  
## Syntaxe  
  
```  
IEnumDebugThreads2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le moteur \(DE\) de débogage implémente cette interface pour représenter une liste de threads dans un programme.  
  
## Remarques pour les appelants  
 Appelez [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) pour obtenir cette interface représentant une liste de tous les threads de tous les programmes s'exécutant dans un processus.  Appelez [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) pour obtenir cette interface représentant une liste de threads qui s'exécutent dans un programme.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IEnumDebugThreads2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Suivant](../Topic/IEnumDebugThreads2::Next.md)|Récupère un nombre spécifié de threads dans la séquence d'énumération.|  
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Ignore un nombre spécifié de threads dans une séquence d'énumération.|  
|[Réinitialiser](../Topic/IEnumDebugThreads2::Reset.md)|réinitialise une séquence d'énumération au début.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Crée un énumérateur qui contient le même état d'énumération que le planificateur actuel.|  
|[GetCount](../Topic/IEnumDebugThreads2::GetCount.md)|Obtient le nombre de threads dans un énumérateur.|  
  
## Notes  
 Visual Studio correspond en général cette interface pour mettre à jour la fenêtre de **Threads** ainsi que pour obtenir le premier thread de la liste, afin d'appeler [Exécuter](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [Continuer](../../../extensibility/debugger/reference/idebugprocess3-continue.md), et [Étape](../../../extensibility/debugger/reference/idebugprocess3-step.md).  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [Étape](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [Continuer](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [Exécuter](../../../extensibility/debugger/reference/idebugprocess3-execute.md)