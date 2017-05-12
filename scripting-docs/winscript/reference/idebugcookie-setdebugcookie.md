---
title: "IDebugCookie::SetDebugCookie | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugCookie.SetDebugCookie
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugCookie::SetDebugCookie"
ms.assetid: 9cba3b05-ff81-4fb0-9382-e9338cb9192d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCookie::SetDebugCookie
Définit le cookie d'application de débogage.  
  
## Syntaxe  
  
```  
HRESULT SetDebugCookie(  
   DWORD  dwDebugAppCookie  
);  
```  
  
#### Paramètres  
 `dwDebugAppCookie`  
 \[in\]  un cookie qui identifie l'application de débogage.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode définit le cookie d'application de débogage, qui permet plusieurs débogueur à s'attacher à un processus.  
  
## Voir aussi  
 [IDebugCookie, interface](../../winscript/reference/idebugcookie-interface.md)