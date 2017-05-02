---
title: "IRemoteDebugApplicationThread::GetState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.GetState
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::GetState"
ms.assetid: 44503a78-efa9-4fbf-98be-a5dcfa329c5a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::GetState
Obtient l'état de ce thread.  
  
## Syntaxe  
  
```  
HRESULT GetState(  
   DWORD*  pState  
);  
```  
  
#### Paramètres  
 `pState`  
 \[out\]  combinaison des balises suivantes d'état du thread :  
  
|Constante|Valeur|Description|  
|---------------|------------|-----------------|  
|THREAD\_STATE\_RUNNING|0x00000001|Le thread s'exécute.|  
|THREAD\_STATE\_SUSPENDED|0x00000002|Le thread est suspendu.|  
|THREAD\_BLOCKED|0x00000004|Le thread est bloqué.|  
|THREAD\_OUT\_OF\_CONTEXT|0x00000008|Le thread est en dehors de contenu.|  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode passe l'état de ce thread.  
  
## Voir aussi  
 [IRemoteDebugApplicationThread, interface](../../winscript/reference/iremotedebugapplicationthread-interface.md)