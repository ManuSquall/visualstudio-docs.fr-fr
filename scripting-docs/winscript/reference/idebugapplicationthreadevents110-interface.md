---
title: "IDebugApplicationThreadEvents110 (interface) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThreadEvents110 (interface)"
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplicationThreadEvents110 (interface)
Ajoute des événements de thread.  Ces événements sont locaux uniquement.  Autrement dit, vous pouvez vous abonner à ces derniers uniquement dans le processus en cours de débogage, [IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738) à l'aide de les méthodes de notifier et d'unadvise sur les objets thread d'application de PDM \(les objets qui implémentent [IDebugApplicationThread, interface](../../winscript/reference/idebugapplicationthread-interface.md)\).  Ils se produisent sur le thread qu'ils proviennent de.  
  
> [!IMPORTANT]
>  Cette interface est implémentée par PDM v11.0 et supérieur.  Trouvé dans activdbg100.h.  
  
## Méthodes  
 L'interface `IDebugActivationThreadEvents110` expose les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Un appel dans le thread à l'aide de le basculement du thread du PDM a démarré.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|Le thread reprend d'un point d'arrêt et sera actif à nouveau.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|Le thread s'interrompt pour un point d'arrêt et peut traiter des appels qui nécessitent que le thread soit complètement interrompu.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Un appel dans le thread à l'aide de le basculement du thread du PDM terminé.|