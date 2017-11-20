---
title: IMachineDebugManagerCookie (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IMachineDebugManagerCookie interface
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a03b959a7eb09f3b85530bbba07d1d2dc7f8948a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanagercookie-interface"></a>IMachineDebugManagerCookie, interface
Similaire à la `IMachineDebugManager` interface, le `IMachineDebugManagerCookie` interface prend en charge les cookies de débogage.  
  
 Cette interface (avec le `IDebugCookie` interface) autoriser les scripts à exécuter dans un processus de débogueur de script sans nécessiter que le débogueur effectuer le suivi de ces scripts.  
  
 Un débogueur de script appelle le `IDebugCookie::SetDebugCookie` méthode sur le Gestionnaire de processus de débogage (PDM). Puis, PDM envoie ce cookie, ainsi que toute demande pour ajouter ou supprimer une application de script vers ou à partir de la Machine Debug Manager (MDM), utilisez les méthodes de la `IMachineDebugManagerCookie` interface. La gestion des appareils mobiles puis avertit chaque débogueur de la modification, à l’exception de celui qui a ce cookie.  
  
 Outre les méthodes héritées de `IUnknown`, le `IMachineDebugManagerCookie` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Ajoute une application en cours d’exécution la liste des applications.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Retourne un énumérateur de la liste actuelle des applications en cours d’exécution.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Supprime une application en cours d’exécution la liste des applications.|  
  
## <a name="see-also"></a>Voir aussi  
 [IMachineDebugManager (Interface)](../../winscript/reference/imachinedebugmanager-interface.md)   
 [Interface IDebugCookie](../../winscript/reference/idebugcookie-interface.md)