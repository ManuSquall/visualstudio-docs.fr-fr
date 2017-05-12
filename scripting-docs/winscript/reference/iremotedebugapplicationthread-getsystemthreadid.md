---
title: "IRemoteDebugApplicationThread::GetSystemThreadId | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.GetSystemThreadId
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::GetSystemThreadId"
ms.assetid: 6a6d5f62-4f60-4e87-9206-3c6f2e026d11
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::GetSystemThreadId
Retourne un identificateur de fonctionnement\-système\- dépendant associé au thread.  
  
## Syntaxe  
  
```  
HRESULT GetSystemThreadId(  
   DWORD*  dwThreadId  
);  
```  
  
#### Paramètres  
 `dwThreadId`  
 \[out\]  Un identificateur de fonctionnement\-système\- dépendant associé au thread.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 La valeur d' `dwThreadId` n'a pas besoin d'être unique sur plusieurs ordinateurs.  
  
## Voir aussi  
 [IRemoteDebugApplicationThread, interface](../../winscript/reference/iremotedebugapplicationthread-interface.md)