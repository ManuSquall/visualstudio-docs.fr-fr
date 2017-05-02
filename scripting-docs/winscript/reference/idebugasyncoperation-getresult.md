---
title: "IDebugAsyncOperation::GetResult | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugAsyncOperation.GetResult
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugAsyncOperation::GetResult"
ms.assetid: 56d43365-6b12-4213-a97c-953c40d7b7f6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperation::GetResult
Fournit la valeur de retour et le paramètre d'objet de retour de l'opération de débogage synchrone.  
  
## Syntaxe  
  
```  
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### Paramètres  
 `phrResult`  
 \[out\]  Si l'opération est terminée, `phrResult` est la valeur de retour d' `IDebugSyncOperation::Execute`.  
  
 `ppunkResult`  
 \[out\]  Si l'opération est terminée, `ppunkResult` est le paramètre de l'objet retourné par l'exécution.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_PENDING`|L'opération ne s'est pas terminée.|  
  
## Notes  
 Si l'opération est terminée, les cette méthode retourne `HRESULT` et le paramètre d'objet d' `IDebugSyncOperation::Execute`.  
  
## Voir aussi  
 [IDebugAsyncOperation, interface](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)