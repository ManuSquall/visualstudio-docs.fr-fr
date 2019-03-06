---
title: Interface IDebugCookie | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 6d47995fbf6c713af0f1d0213dbf5c3c98d54a0e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344025"
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