---
title: "IDebugAsyncOperation::QueryIsComplete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugAsyncOperation.QueryIsComplete
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugAsyncOperation::QueryIsComplete"
ms.assetid: fcf6e229-4d40-46d9-ab81-d3561bc8e084
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperation::QueryIsComplete
Détermine si l'opération de débogage est terminée.  
  
## Syntaxe  
  
```  
HRESULT QueryIsComplete();  
```  
  
#### Paramètres  
 Cette méthode n'accepte pas de paramètres.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|L'opération est terminée.|  
|`S_FALSE`|L'opération n'est pas terminée.|  
  
## Notes  
 Cette méthode détermine si l'opération de débogage est terminée.  
  
## Voir aussi  
 [IDebugAsyncOperation, interface](../../winscript/reference/idebugasyncoperation-interface.md)