---
title: Interface IMachineDebugManagerCookie | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerCookie interface
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b39c286f389c99187b0f3250fc68af92ff5dcc8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573885"
---
# <a name="imachinedebugmanagercookie-interface"></a>IMachineDebugManagerCookie, interface
À l’instar de l’interface `IMachineDebugManager`, l’interface `IMachineDebugManagerCookie` prend en charge les cookies de débogage.  
  
 Cette interface (avec l’interface `IDebugCookie`) permet aux scripts de s’exécuter dans un processus de débogueur de script sans exiger que le débogueur effectue le suivi de ces scripts.  
  
 Un débogueur de script appelle la méthode `IDebugCookie::SetDebugCookie` sur le gestionnaire de débogage de processus (PDM). Ensuite, le PDM envoie ce cookie avec toute demande d’ajout ou de suppression d’une application de script vers ou à partir de machine Debug Manager (MDM), à l’aide des méthodes de l’interface `IMachineDebugManagerCookie`. Le MDM notifie ensuite chaque débogueur de la modification, à l’exception de celui qui contient ce cookie.  
  
 En plus des méthodes héritées de `IUnknown`, l’interface `IMachineDebugManagerCookie` expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Ajoute une application à la liste des applications en cours d’exécution.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Retourne un énumérateur de la liste actuelle des applications en cours d’exécution.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Supprime une application de la liste des applications en cours d’exécution.|  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IMachineDebugManager](../../winscript/reference/imachinedebugmanager-interface.md)  
 [Interface IDebugCookie](../../winscript/reference/idebugcookie-interface.md)