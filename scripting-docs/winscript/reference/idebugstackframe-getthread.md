---
title: "IDebugStackFrame::GetThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrame.GetThread
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrame::GetThread"
ms.assetid: ece24728-a6b2-4b01-a6f0-0a82b15be39b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrame::GetThread
Retourne le thread associé à ce frame de pile.  
  
## Syntaxe  
  
```  
HRESULT GetThread(  
   IDebugApplicationThread**  ppat  
);  
```  
  
#### Paramètres  
 `ppat`  
 \[out\]  Le thread associé à ce frame de pile.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode retourne le thread associé à ce frame de pile.  
  
## Voir aussi  
 [IDebugStackFrame, interface](../../winscript/reference/idebugstackframe-interface.md)