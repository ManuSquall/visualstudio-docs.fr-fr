---
title: "IRemoteDebugApplication110::GetMainThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplication110::GetMainThread"
ms.assetid: 9982acc9-3d35-4dcf-8ca9-662469de4072
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IRemoteDebugApplication110::GetMainThread
Retourne le thread principal pour les hôtes qui appellent [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439), sinon retourne E\_FAIL.  
  
> [!IMPORTANT]
>  [IRemoteDebugApplication, interface](../../winscript/reference/iremotedebugapplication-interface.md) est implémenté par PDM v11.0 et supérieur.  Trouvé dans activdbg100.h.  
  
## Syntaxe  
  
```cpp  
HRESULT GetMainThread([out] IRemoteDebugApplicationThread **ppThread);  
  
```  
  
#### Paramètres  
 `ppThread`  
 \[out\]  [IRemoteDebugApplicationThread, interface](../../winscript/reference/iremotedebugapplicationthread-interface.md)principal.  
  
## Voir aussi  
 [IRemoteDebugApplication, interface](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110 \(interface\)](../../winscript/reference/iremotedebugapplication110-interface.md)