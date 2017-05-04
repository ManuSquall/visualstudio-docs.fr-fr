---
title: "IDebugApplicationThread110::GetActiveThreadRequestCount | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread110::GetActiveThreadRequestCount"
ms.assetid: 025d2072-1d7f-4448-8aa3-38a014313570
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugApplicationThread110::GetActiveThreadRequestCount
Retourne le nombre de demandes de thread les mécanismes de basculement du thread du PDM actuellement sont traités.  Ce nombre est habituellement 0 ou 1.  Toutefois, le nombre peut être plus élevé si un appel de thread commence à traiter mais déclencheurs un synchrone pour exiger du thread, ou interrompt sinon le thread et permet des appels entrant à traiter de nouveau \(par exemple, lors de le déclenchement d'un événement d' [IRemoteDebugApplicationEvents, interface](../../winscript/reference/iremotedebugapplicationevents-interface.md) , qui est émis sur le thread du débogueur\).  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110 \(interface\)](../../winscript/reference/idebugapplicationthread110-interface.md) est implémenté par PDM v11.0 et supérieur.  Trouvé dans activdbg100.h.  
  
## Syntaxe  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
  
```  
  
#### Paramètres  
 `puiThreadRequests`  
 \[out\]  Le nombre de demandes de thread.  
  
## Voir aussi  
 [IDebugApplicationThread110 \(interface\)](../../winscript/reference/idebugapplicationthread110-interface.md)