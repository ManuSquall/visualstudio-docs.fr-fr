---
title: Interface IDebugApplicationThreadEvents110 | Microsoft Docs
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
ms.openlocfilehash: 5dd666d825c40155675714f5945209f22198993c
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984391"
---
# <a name="idebugapplicationthreadevents110-interface"></a>IDebugApplicationThreadEvents110 (interface)
Ajoute d’autres événements de thread. Ces événements sont locaux uniquement. Autrement dit, vous ne pouvez vous y abonner que dans le processus en cours de débogage, à l’aide des méthodes [IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint) Advise et Unadvise sur les objets de thread d’application PDM (objets qui implémentent l' [interface IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)). Ils se produisent sur le thread à partir duquel ils proviennent.  
  
> [!IMPORTANT]
> Elle est implémentée par PDM version v11.0 et supérieures. Trouvée dans activdbg100.h.  
  
## <a name="methods"></a>Méthodes  
 L'interface `IDebugActivationThreadEvents110` expose les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Un appel dans le thread à l’aide du basculement de thread de PDM a commencé.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|Le thread reprend à partir d’un point d’arrêt et sera à nouveau actif.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|Le thread s’interrompt pour un point d’arrêt et peut gérer les appels qui requièrent l’interruption totale du thread.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Un appel dans le thread à l’aide du basculement de thread de PDM est terminé.|