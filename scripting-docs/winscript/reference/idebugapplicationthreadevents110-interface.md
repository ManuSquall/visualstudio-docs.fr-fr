---
title: IDebugApplicationThreadEvents110 (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplicationThreadEvents110 Interface
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aaf312b1730696b812172aeea175619e911d03a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthreadevents110-interface"></a>IDebugApplicationThreadEvents110 (interface)
Ajoute plusieurs événements de thread. Ces événements sont locales uniquement. Autrement dit, vous pouvez vous y abonner uniquement dans le processus en cours de débogage, à l’aide de la [IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738) de notifications et de déconseiller des méthodes sur des objets de thread d’application PDM (des objets qui implémentent [IDebugApplicationThread Interface](../../winscript/reference/idebugapplicationthread-interface.md)). Elles se produisent sur le thread de qu'origine.  
  
> [!IMPORTANT]
>  Elle est implémentée par PDM version v11.0 et supérieures. Trouvée dans activdbg100.h.  
  
## <a name="methods"></a>Méthodes  
 L'interface `IDebugActivationThreadEvents110` expose les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Un appel dans le thread à l’aide du thread de PDM commutation a commencé.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|Le thread est reprise à partir d’un point d’arrêt et sera à nouveau actif.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|Le thread est interrompu pour un point d’arrêt et peut traiter des appels qui nécessitent le thread est suspendu entièrement.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Un appel dans le thread à l’aide du thread de PDM commutation est terminée.|