---
title: "IDebugAsyncOperationCallBack::onComplete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugAsyncOperationCallBack.onComplete
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugAsyncOperationCallBack::onComplete"
ms.assetid: d4023f5a-41f9-4948-b0dc-3317d61bb783
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperationCallBack::onComplete
Signale qu'un résultat est disponible à partir d'une opération de débogage asynchrone.  
  
## Syntaxe  
  
```  
HRESULT onComplete();  
```  
  
#### Paramètres  
 Cette méthode n'accepte pas de paramètres.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode signale qu'un résultat est disponible à partir d'un objet d' `IDebugAsyncOperation` .  Déclenche les d'événements dans le thread du débogueur.  
  
## Voir aussi  
 [IDebugAsyncOperationCallBack, interface](../../winscript/reference/idebugasyncoperationcallback-interface.md)   
 [IDebugAsyncOperation, interface](../../winscript/reference/idebugasyncoperation-interface.md)