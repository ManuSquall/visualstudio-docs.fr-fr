---
title: Interface IDebugCookie | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugCookie interface
ms.assetid: 0dbc75d9-6f33-400f-a5bf-9122cf534082
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ee129526113a1c8af8f918de81c1f286d5cb703
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974512"
---
# <a name="idebugcookie-interface"></a>IDebugCookie, interface
Permet le cookie de débogage à définir, pour une utilisation avec le `IMachineDebugManagerCookie` interface. Pour plus d’informations, consultez [IMachineDebugManagerCookie (Interface)](../../winscript/reference/imachinedebugmanagercookie-interface.md). Cette interface est implémentée par le Gestionnaire de processus déboguer (PDM) et consommée par les débogueurs de script.  
  
## <a name="methods"></a>Méthodes  
 Outre les méthodes héritées de `IUnknown`, le `IDebugCookie` interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugCookie::SetDebugCookie](../../winscript/reference/idebugcookie-setdebugcookie.md)|Définit le cookie d’application de débogage.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IMachineDebugManagerCookie](../../winscript/reference/imachinedebugmanagercookie-interface.md)