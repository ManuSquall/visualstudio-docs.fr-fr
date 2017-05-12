---
title: "IDebugApplicationThread::SynchronousCallIntoThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationThread.SynchronousCallIntoThread
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationThread::SynchronousCallIntoThread"
ms.assetid: 8a91157f-dade-418a-ad02-5607ce12c95c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationThread::SynchronousCallIntoThread
Fournit un mécanisme pour l'appel au code exécuté dans le thread d'application.  
  
## Syntaxe  
  
```  
HRESULT SynchronousCallIntoThread(  
   IDebugThreadCall*  pstcb,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### Paramètres  
 `pstcb`  
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
 Cette méthode fournit un mécanisme pour l'appel au code exécuté dans le thread du débogueur.  Les moteurs de langage et les hôtes utilisent en général cette méthode pour implémenter les objets libres de threads sur leurs implémentations filetées unique.  
  
## Voir aussi  
 [IDebugApplicationThread, interface](../../winscript/reference/idebugapplicationthread-interface.md)   
 [IDebugThreadCall, interface](../../winscript/reference/idebugthreadcall-interface.md)