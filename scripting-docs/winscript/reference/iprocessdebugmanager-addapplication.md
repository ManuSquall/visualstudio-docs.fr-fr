---
title: "IProcessDebugManager::AddApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProcessDebugManager.AddApplication
apilocation: pdm.dll
helpviewer_keywords: 
  - "IProcessDebugManager::AddApplication"
ms.assetid: 73828299-11eb-4c58-ad70-f80f2d0eede8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager::AddApplication
Ajoute une application sur l'ordinateur de débogage la liste du gestionnaire d'applications actives.  
  
## Syntaxe  
  
```  
HRESULT AddApplication(  
   IDebugApplication*  pda,  
   DWORD*              pdwAppCookie  
);  
```  
  
#### Paramètres  
 `pda`  
 \[in\]  L'application de débogage à ajouter à la liste d'applications actives.  
  
 `pdwAppCookie`  
 \[out\]  Un cookie utilisé pour supprimer l'application de l'ordinateur de débogage le gestionnaire.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode ajoute une application à la liste d'application en cours de exécution sur l'ordinateur de débogage le gestionnaire.  
  
## Voir aussi  
 [IProcessDebugManager, interface](../../winscript/reference/iprocessdebugmanager-interface.md)   
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)