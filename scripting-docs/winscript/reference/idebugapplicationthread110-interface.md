---
title: "IDebugApplicationThread110 (interface) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread110 (interface)"
ms.assetid: 25bc351f-3451-4387-9302-078f6292ddff
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplicationThread110 (interface)
Fournit des fonctionnalités pour l'interface d' [IDebugApplicationThread, interface](../../winscript/reference/idebugapplicationthread-interface.md) .  
  
> [!IMPORTANT]
>  Cette interface est implémentée par PDM v11.0 et supérieur.  Trouvé dans activdbg100.h.  
  
## Méthodes  
 L'interface `IDebugApplicationThread110` expose les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugApplicationThread110::AsynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread110-asynchronouscallintothread.md)|Effectue un appel asynchrone sur le thread principal.|  
|[IDebugApplicationThread110::GetActiveThreadRequestCount](../../winscript/reference/idebugapplicationthread110-getactivethreadrequestcount.md)|Un nombre le thread de demandes des mécanismes de basculement du thread du PDM processus actuel.  Habituellement 0 ou 1, mais il est possible de faire pour être plus élevé si un appel de thread commence à traiter mais pour des déclencheurs un synchrone nécessiter du thread ou interrompt sinon le thread \(par exemple, lors de le déclenchement d'un événement d'IDebugApplicationEvents émis sur le thread du débogueur\)|  
|[IDebugApplicationThread110::IsSuspendedForBreakPoint](../../winscript/reference/idebugapplicationthread110-issuspendedforbreakpoint.md)|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) a été appelé sur ce thread et ne s'est pas encore terminé.|  
|[IDebugApplicationThread110::IsThreadCallable](../../winscript/reference/idebugapplicationthread110-isthreadcallable.md)|Ce thread est dans un état qui peut traiter des appels effectués à l'aide de mécanismes de basculement du thread du PDM \(tels que SynchronousCallInThread\).|