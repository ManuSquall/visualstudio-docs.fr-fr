---
title: IDebugApplicationThreadEvents110 Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110 Interface
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0051f18c67fffc9801ad326745a0dc9dd63f4391
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148852"
---
# <a name="idebugapplicationthreadevents110-interface"></a>IDebugApplicationThreadEvents110 (interface)
Ajoute plusieurs événements de thread. Ces événements sont locales uniquement. Autrement dit, vous pouvez vous y abonner uniquement dans le processus en cours de débogage, à l’aide de la [IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738) et désinformation des méthodes sur des objets de thread d’application PDM (objets qui implémentent [IDebugApplicationThread Interface](../../winscript/reference/idebugapplicationthread-interface.md)). Elles se produisent sur le thread de qu'origine.  
  
> [!IMPORTANT]
>  Elle est implémentée par PDM version v11.0 et supérieures. Trouvée dans activdbg100.h.  
  
## <a name="methods"></a>Méthodes  
 L'interface `IDebugActivationThreadEvents110` expose les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Un appel dans le thread à l’aide du thread de PDM commutation a commencé.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|Le thread reprend à partir d’un point d’arrêt et est actif une fois encore.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|Le thread est en suspension pour un point d’arrêt et peut gérer des appels qui nécessitent le thread doit être suspendu entièrement.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Un appel dans le thread à l’aide du thread de PDM commutation s’est terminée.|