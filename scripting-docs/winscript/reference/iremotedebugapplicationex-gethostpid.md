---
title: "IRemoteDebugApplicationEx:GetHostPid | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEx:GetHostPid
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEx:GetHostPid"
ms.assetid: 4cf9f46c-29cf-4201-87f0-5b1ddbed2f2b
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplicationEx:GetHostPid
Retourne l'ID de processus pour l'application hôte.  
  
## Syntaxe  
  
```  
HRESULT GetHostPid(  
   DWORD*  dwHostPid  
);  
```  
  
#### Paramètres  
 `dwHostPid`  
 \[out\]  l'identificateur de processus hôte.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Utilisé par l'IDE.  
  
## Voir aussi  
 [IRemoteDebugApplicationEx Interface](http://msdn.microsoft.com/fr-fr/2f65fa67-06b7-4053-8945-22383ab66343)