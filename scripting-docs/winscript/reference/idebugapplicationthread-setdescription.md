---
title: "IDebugApplicationThread::SetDescription | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationThread.SetDescription
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationThread::SetDescription"
ms.assetid: 084e5b74-af95-41b4-ae55-01f6f4d22168
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationThread::SetDescription
Définit la description de ce thread.  
  
## Syntaxe  
  
```  
HRESULT SetDescription(  
   LPCOLESTR  pstrDescription  
);  
```  
  
#### Paramètres  
 `pstrDescription`  
 \[in\]  La description de ce thread.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode définit la description de ce thread.  
  
## Voir aussi  
 [IDebugApplicationThread, interface](../../winscript/reference/idebugapplicationthread-interface.md)