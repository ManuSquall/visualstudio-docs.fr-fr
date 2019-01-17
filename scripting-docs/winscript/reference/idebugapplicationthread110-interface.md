---
title: Interface IDebugApplicationThread110 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110 Interface
ms.assetid: 25bc351f-3451-4387-9302-078f6292ddff
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 170b345bdb4587d1fd29c1f0f906df0157abd877
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348917"
---
# <a name="idebugapplicationthread110-interface"></a>IDebugApplicationThread110 (interface)
Offre davantage de fonctionnalités pour le [IDebugApplicationThread (Interface)](../../winscript/reference/idebugapplicationthread-interface.md) interface.  
  
> [!IMPORTANT]
>  Elle est implémentée par PDM version v11.0 et supérieures. Trouvée dans activdbg100.h.  
  
## <a name="methods"></a>Méthodes  
 L'interface `IDebugApplicationThread110` expose les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugApplicationThread110::AsynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread110-asynchronouscallintothread.md)|Effectue un appel asynchrone sur le thread principal.|  
|[IDebugApplicationThread110::GetActiveThreadRequestCount](../../winscript/reference/idebugapplicationthread110-getactivethreadrequestcount.md)|Décompte du nombre de demandes de thread du thread de responsables prestations Professional direct des mécanismes de basculement en cours de traitement. Généralement 0 ou 1, de possibles pour cette option pour être plus élevé si un appel du thread démarre le traitement, mais déclenche un appel synchrone en dehors du thread ou sinon suspend le thread (par exemple, en déclenchant un événement IDebugApplicationEvents qui est émis sur le débogueur thread)|  
|[IDebugApplicationThread110::IsSuspendedForBreakPoint](../../winscript/reference/idebugapplicationthread110-issuspendedforbreakpoint.md)|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) a été appelé sur ce thread et n’est pas encore terminée.|  
|[IDebugApplicationThread110::IsThreadCallable](../../winscript/reference/idebugapplicationthread110-isthreadcallable.md)|Ce thread est dans un état qui peut traiter des appels effectués à l’aide du thread de PDM commutation mécanismes (par exemple, SynchronousCallInThread).|