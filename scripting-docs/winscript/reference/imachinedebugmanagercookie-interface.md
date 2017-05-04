---
title: "IMachineDebugManagerCookie, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IMachineDebugManagerCookie (interface)"
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManagerCookie, interface
Semblable à l'interface d' `IMachineDebugManager` , prend en charge d'interface d' `IMachineDebugManagerCookie` debug des cookies.  
  
 Cette interface \(avec l'interface d' `IDebugCookie` \) permettent des scripts à s'exécuter dans un processus de débogage de script sans que le débogueur contiennent ces scripts.  
  
 Un débogueur de script appelle la méthode d' `IDebugCookie::SetDebugCookie` sur Process Debug Manager \(PDM\).  Ensuite, le PDM envoie ce cookie avec toute demande d'ajouter ou de supprimer une application de script à partir de Debug Machine Manager \(MDM\), à l'aide de les méthodes d'interface d' `IMachineDebugManagerCookie` .  Le MDM informe chaque débogueur de la modification, à l'exception de celle qui a ce cookie.  
  
 Outre les méthodes héritées de `IUnknown`, l'interface `IMachineDebugManagerCookie` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Ajoute une application à la liste d'application active.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Retourne un énumérateur de la liste actuelle d'applications actives.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Supprime une application de la liste d'application active.|  
  
## Voir aussi  
 [IMachineDebugManager, interface](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IDebugCookie, interface](../../winscript/reference/idebugcookie-interface.md)