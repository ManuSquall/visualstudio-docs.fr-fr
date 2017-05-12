---
title: "IRemoteDebugApplicationThread::SetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.SetNextStatement
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::SetNextStatement"
ms.assetid: 356766da-f7b7-4e8d-b4f3-2ab8da0609b8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::SetNextStatement
Exécution de force à continuer aussi proche que possible de le contexte de code donné, dans le contexte du frame donné.  
  
## Syntaxe  
  
```  
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### Paramètres  
 `pStackFrame`  
 \[in\]  L'objet frame de pile.  Cet argument peut être NULL, qui implique le frame de pile actuel doit être utilisé.  
  
 `pCodeContext`  
 \[in\]  le contexte de code.  Cet argument peut être NULL, qui implique le contexte de code actuel doit être utilisé.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode force l'exécution pour continuer aussi proche que possible de le contexte de code spécifié par `pCodeContext`, dans le contexte du frame spécifié par `pStackFrame`.  L'un ou l'autre de ces arguments peut être `NULL`, qui représente le frame ou le contexte actuel.  
  
## Voir aussi  
 [IRemoteDebugApplicationThread, interface](../../winscript/reference/iremotedebugapplicationthread-interface.md)