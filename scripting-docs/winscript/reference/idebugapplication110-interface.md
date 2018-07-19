---
title: IDebugApplication110 (Interface) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110 Interface
ms.assetid: ae943133-eb65-4ddc-a29f-9280a82dd8d6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd7c283e925db5b42b4d04bfc42ea087ecc22b6f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726059"
---
# <a name="idebugapplication110-interface"></a>IDebugApplication110 (interface)
Le `IDebugApplication110` interface étend les fonctionnalités de la [IDebugApplication (Interface)](../../winscript/reference/idebugapplication-interface.md). Vous pouvez obtenir une instance de cette interface en appelant QueryInterface sur une implémentation de [IDebugApplication (Interface)](../../winscript/reference/idebugapplication-interface.md).  
  
> [!IMPORTANT]
>  Elle est implémentée par PDM version v11.0 et supérieures. Trouvée dans activdbg100.h.  
  
## <a name="methods"></a>Méthodes  
 L'interface `IDebugApplication110` expose les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugApplication110::SynchronousCallInMainThread](../../winscript/reference/idebugapplication110-synchronouscallinmainthread.md)|Effectue un appel synchrone sur le thread principal.|  
|[IDebugApplication110::AsynchronousCallInMainThread](../../winscript/reference/idebugapplication110-asynchronouscallinmainthread.md)|Effectue un appel asynchrone sur le thread principal.|  
|[IDebugApplication110::CallableWaitForHandles](../../winscript/reference/idebugapplication110-callablewaitforhandles.md)|Attend qu’une des poignées spécifiées soit signalé tout en autorisant inter-threads appelle publication sur ce thread. Cette méthode doit être appelée à partir du thread de débogueur.|