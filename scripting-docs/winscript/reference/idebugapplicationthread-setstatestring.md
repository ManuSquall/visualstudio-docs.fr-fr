---
title: "IDebugApplicationThread::SetStateString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationThread.SetStateString
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationThread::SetStateString"
ms.assetid: a59001d5-ea00-4fd0-bb20-0b592d9c795d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationThread::SetStateString
Définit la description de l'état du thread.  
  
## Syntaxe  
  
```  
HRESULT SetStateString(  
   LPCOLESTR  pstrState  
);  
```  
  
#### Paramètres  
 `pstrState`  
 \[in\]  la description de l'état du thread.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode définit la description de l'état du thread.  
  
## Voir aussi  
 [IDebugApplicationThread, interface](../../winscript/reference/idebugapplicationthread-interface.md)