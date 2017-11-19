---
title: IRemoteDebugApplicationEvents (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IRemoteDebugApplicationEvents interface
ms.assetid: 9626519e-910c-48e0-ae99-c711ce6628fd
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04d40d3e03cfb9582075ec1be7abace963d1377f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationevents-interface"></a>IRemoteDebugApplicationEvents, interface
Le `IRemoteDebugApplicationEvents` est l’interface d’événement fournie par une application de débogage. Cette interface est toujours appelée à partir du thread de débogueur.  
  
 Outre les méthodes héritées de `IUnknown`, le `IRemoteDebugApplicationEvents` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IRemoteDebugApplicationEvents::OnConnectDebugger](../../winscript/reference/iremotedebugapplicationevents-onconnectdebugger.md)|Gère un débogueur connecter l’événement.|  
|[IRemoteDebugApplicationEvents::OnDisconnectDebugger](../../winscript/reference/iremotedebugapplicationevents-ondisconnectdebugger.md)|Gère un débogueur de la déconnexion.|  
|[IRemoteDebugApplicationEvents::OnSetName](../../winscript/reference/iremotedebugapplicationevents-onsetname.md)|Gère un événement de nom de jeu.|  
|[IRemoteDebugApplicationEvents::OnDebugOutput](../../winscript/reference/iremotedebugapplicationevents-ondebugoutput.md)|Gère un événement de sortie du débogueur.|  
|[IRemoteDebugApplicationEvents::OnClose](../../winscript/reference/iremotedebugapplicationevents-onclose.md)|Gère un événement fermer une application.|  
|[IRemoteDebugApplicationEvents::OnEnterBreakPoint](../../winscript/reference/iremotedebugapplicationevents-onenterbreakpoint.md)|Gère un événement pour l’entrée d’un point d’arrêt.|  
|[IRemoteDebugApplicationEvents::OnLeaveBreakPoint](../../winscript/reference/iremotedebugapplicationevents-onleavebreakpoint.md)|Gère un événement de conserver un point d’arrêt.|  
|[IRemoteDebugApplicationEvents::OnCreateThread](../../winscript/reference/iremotedebugapplicationevents-oncreatethread.md)|Gère un événement de thread de création.|  
|[IRemoteDebugApplicationEvents::OnDestroyThread](../../winscript/reference/iremotedebugapplicationevents-ondestroythread.md)|Gère un événement de destruction de threads.|  
|[IRemoteDebugApplicationEvents::OnBreakFlagChange](../../winscript/reference/iremotedebugapplicationevents-onbreakflagchange.md)|Gère un événement lorsque les indicateurs de saut changent.|