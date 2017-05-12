---
title: "IDebugApplication::SetName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.SetName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::SetName"
ms.assetid: 7b0ddc58-6f20-4ce3-9bdf-81a6c1d64256
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::SetName
Définit le nom de l'application.  
  
## Syntaxe  
  
```  
HRESULT SetName(  
   LPCOLESTR  pstrName  
);  
```  
  
#### Paramètres  
 `pstrName`  
 \[in\] Nom de l'application.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Nom fourni à cette méthode est retourné dans les appels suivants à la méthode d' `IRemoteDebugApplication::GetName` .  
  
 Cette méthode doit être appelée avant d'appeler la méthode d' `IProcessDebugManager::AddApplication` .  
  
## Voir aussi  
 [IDebugApplication, interface](../../winscript/reference/idebugapplication-interface.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)