---
title: Interface IApplicationDebugger | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IApplicationDebugger interface
ms.assetid: 27f6f8f5-2bf3-49bc-8abb-dfca98935aba
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b364422afcdf72deaee3d56123a71672769ed61
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348319"
---
# <a name="iapplicationdebugger-interface"></a>IApplicationDebugger, interface
Interface principale exposée par un débogueur. Outre les méthodes héritées de `IUnknown`, le `IApplicationDebugger` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IApplicationDebugger::QueryAlive](../../winscript/reference/iapplicationdebugger-queryalive.md)|Indique si le débogueur est réactif.|  
|[IApplicationDebugger::CreateInstanceAtDebugger](../../winscript/reference/iapplicationdebugger-createinstanceatdebugger.md)|Permet la création d’objets dans le processus du débogueur par le code qui est out-of-process au débogueur.|  
|[IApplicationDebugger::onDebugOutput](../../winscript/reference/iapplicationdebugger-ondebugoutput.md)|Gère un événement de sortie de débogage.|  
|[IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)|Gère un événement de point d’arrêt.|  
|[IApplicationDebugger::onClose](../../winscript/reference/iapplicationdebugger-onclose.md)|Gère un événement close application de débogage.|  
|[IApplicationDebugger::onDebuggerEvent](../../winscript/reference/iapplicationdebugger-ondebuggerevent.md)|Gère un événement d’application personnalisée.|