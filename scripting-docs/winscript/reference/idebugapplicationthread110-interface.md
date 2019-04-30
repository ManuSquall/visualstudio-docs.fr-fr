---
title: Interface IDebugApplicationThread110 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 44df7168c241c9a750354e1a603d6c5ba96dabd2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440546"
---
# <a name="idebugapplicationthread110-interface"></a>IDebugApplicationThread110 (interface)
Offre davantage de fonctionnalités pour le [IDebugApplicationThread (Interface)](../../winscript/reference/idebugapplicationthread-interface.md) interface.  
  
> [!IMPORTANT]
> Elle est implémentée par PDM version v11.0 et supérieures. Trouvée dans activdbg100.h.  
  
## <a name="methods"></a>Méthodes  
 L'interface `IDebugApplicationThread110` expose les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugApplicationThread110::AsynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread110-asynchronouscallintothread.md)|Effectue un appel asynchrone sur le thread principal.|  
|[IDebugApplicationThread110::GetActiveThreadRequestCount](../../winscript/reference/idebugapplicationthread110-getactivethreadrequestcount.md)|Décompte du nombre de demandes de thread du thread de responsables prestations Professional direct des mécanismes de basculement en cours de traitement. Généralement 0 ou 1, de possibles pour cette option pour être plus élevé si un appel du thread démarre le traitement, mais déclenche un appel synchrone en dehors du thread ou sinon suspend le thread (par exemple, en déclenchant un événement IDebugApplicationEvents qui est émis sur le débogueur thread)|  
|[IDebugApplicationThread110::IsSuspendedForBreakPoint](../../winscript/reference/idebugapplicationthread110-issuspendedforbreakpoint.md)|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) a été appelé sur ce thread et n’est pas encore terminée.|  
|[IDebugApplicationThread110::IsThreadCallable](../../winscript/reference/idebugapplicationthread110-isthreadcallable.md)|Ce thread est dans un état qui peut traiter des appels effectués à l’aide du thread de PDM commutation mécanismes (par exemple, SynchronousCallInThread).|