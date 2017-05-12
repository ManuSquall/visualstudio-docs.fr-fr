---
title: "IRemoteDebugApplicationThread::Suspend | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.Suspend
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::Suspend"
ms.assetid: fd5cc874-2970-4092-b1cd-e638775b0e20
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::Suspend
Interrompt le thread.  
  
## Syntaxe  
  
```  
HRESULT Suspend(  
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
 Lorsque cette méthode interrompt le thread, il incrémente le compteur de suspension.  
  
## Voir aussi  
 [IRemoteDebugApplicationThread, interface](../../winscript/reference/iremotedebugapplicationthread-interface.md)