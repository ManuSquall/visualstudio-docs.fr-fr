---
title: "IDebugApplication::SynchronousCallInDebuggerThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.SynchronousCallInDebuggerThread
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::SynchronousCallInDebuggerThread"
ms.assetid: 9daa1722-f25a-4691-aefc-fd28672fb883
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::SynchronousCallInDebuggerThread
Fournit un mécanisme pour l'appel au code exécuté dans le thread du débogueur.  
  
## Syntaxe  
  
```  
HRESULT SynchronousCallInDebuggerThread(  
   IDebugThreadCall*  pptc,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### Paramètres  
 `pptc`  
 \[in\]  l'objet à l'appel.  
  
 `dwParam1`  
 \[in\]  premier paramètre à passer à la méthode d' `IDebugThreadCall::ThreadCallHandler` .  
  
 `dwParam2`  
 \[in\]  deuxième paramètre à passer à la méthode d' `IDebugThreadCall::ThreadCallHandler` .  
  
 `dwParam3`  
 \[in\]  troisième paramètre à passer à la méthode d' `IDebugThreadCall::ThreadCallHandler` .  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Les moteurs de langage et les hôtes utilisent en général cette méthode pour implémenter les objets libres de threads sur leurs implémentations filetées unique.  
  
## Voir aussi  
 [IDebugApplication, interface](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugThreadCall, interface](../../winscript/reference/idebugthreadcall-interface.md)