---
title: "IDebugApplication::CreateAsyncDebugOperation | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.CreateAsyncDebugOperation
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::CreateAsyncDebugOperation"
ms.assetid: bc32b101-6364-4498-8458-bd5f3ab5ad94
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::CreateAsyncDebugOperation
Fournit l'accès à une opération asynchrone de débogage synchrone donnée.  
  
## Syntaxe  
  
```  
HRESULT CreateAsyncDebugOperation(  
   IDebugSyncOperation*    psdo,  
   IDebugAsyncOperation**  ppado  
);  
```  
  
#### Paramètres  
 `psdo`  
 \[in\]  l'objet synchrone d'opération de débogage.  
  
 `ppado`  
 \[out\]  l'objet asynchrone d'opération de débogage.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode permet aux moteurs de langage pour évaluer des expressions de façon asynchrone sans synchroniser explicitement avec le thread du débogueur.  Pour plus d'informations, consultez [IDebugSyncOperation, interface](../../winscript/reference/idebugsyncoperation-interface.md) et [IDebugAsyncOperation, interface](../../winscript/reference/idebugasyncoperation-interface.md).  
  
## Voir aussi  
 [IDebugApplication, interface](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugSyncOperation, interface](../../winscript/reference/idebugsyncoperation-interface.md)   
 [IDebugAsyncOperation, interface](../../winscript/reference/idebugasyncoperation-interface.md)