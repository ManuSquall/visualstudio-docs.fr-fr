---
title: "IMachineDebugManagerCookie::AddApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IMachineDebugManagerCookie.AddApplication
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IMachineDebugManagerCookie::AddApplication"
ms.assetid: 4d5503c5-aca9-4cf7-9900-f77bf5f3263d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManagerCookie::AddApplication
Ajoute une application à la liste d'application active.  
  
## Syntaxe  
  
```  
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwDebugAppCookie,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### Paramètres  
 `pda`  
 \[in\]  application à la liste d'application active.  
  
 `dwDebugAppCookie`  
 \[in\]  un cookie qui identifie l'application de débogage.  
  
 `pdwAppCookie`  
 \[out\]  Un cookie utilisé pour supprimer l'application de l'ordinateur de débogage le gestionnaire.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode est appelée par le processus de débogage le gestionnaire chaque fois qu' `IProcessDebugManager::AddApplication` est appelé.  
  
## Voir aussi  
 [IMachineDebugManagerCookie, interface](../../winscript/reference/imachinedebugmanagercookie-interface.md)   
 [IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)