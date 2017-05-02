---
title: "IRemoteDebugApplicationThread::Resume | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.Resume
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::Resume"
ms.assetid: ac290861-515d-4f06-b452-3b96f54e538c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::Resume
Continue le thread.  
  
## Syntaxe  
  
```  
HRESULT Resume(  
   DWORD*  pdwCount  
);  
```  
  
#### Paramètres  
 `pdwCount`  
 \[out\]  Le compteur de suspension du thread.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Lorsque cette méthode poursuit le thread, il décrémente le compteur de suspension.  
  
## Voir aussi  
 [IRemoteDebugApplicationThread, interface](../../winscript/reference/iremotedebugapplicationthread-interface.md)