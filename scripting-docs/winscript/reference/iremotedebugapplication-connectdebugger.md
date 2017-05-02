---
title: "IRemoteDebugApplication::ConnectDebugger | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.ConnectDebugger
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::ConnectDebugger"
ms.assetid: ded94101-7efe-466f-aa70-b3e30a38c4d8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::ConnectDebugger
Connecte un débogueur à cette application.  
  
## Syntaxe  
  
```  
HRESULT ConnectDebugger(  
   IApplicationDebugger*  pad  
);  
```  
  
#### Paramètres  
 `pad`  
 \[in\]  Le débogueur à attacher à cette application.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|Un débogueur est déjà connecté à cette application.|  
  
## Notes  
 Une application peut avoir qu'un débogueur connecté à la fois.  Cette méthode échoue si un débogueur est déjà connecté.  
  
## Voir aussi  
 [IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)   
 [IRemoteDebugApplication, interface](../../winscript/reference/iremotedebugapplication-interface.md)