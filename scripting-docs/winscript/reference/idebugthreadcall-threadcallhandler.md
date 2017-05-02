---
title: "IDebugThreadCall::ThreadCallHandler | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugThreadCall.ThreadCallHandler
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugThreadCall::ThreadCallHandler"
ms.assetid: c6d5d9db-bfed-44ec-90bc-46637f7de0ab
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugThreadCall::ThreadCallHandler
Appels de handles pour exécuter du code dans un autre thread.  
  
## Syntaxe  
  
```  
HRESULT ThreadCallHandler(  
   DWORD_PTR  dwParam1,  
   DWORD_PTR  dwParam2,  
   DWORD_PTR  dwParam3  
);  
```  
  
#### Paramètres  
 `dwParam1`  
 \[in\]  le premier paramètre.  
  
 `dwParam2`  
 \[in\]  le deuxième paramètre.  
  
 `dwParam3`  
 \[in\]  le troisième paramètre.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode traite des appels pour exécuter du code dans le thread du débogueur.  
  
## Voir aussi  
 [IDebugThreadCall, interface](../../winscript/reference/idebugthreadcall-interface.md)   
 [IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)   
 [IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)