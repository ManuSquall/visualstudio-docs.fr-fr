---
title: "IDebugSyncOperation::Execute | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSyncOperation.Execute
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugSyncOperation::Execute"
ms.assetid: a45b8c7d-c51a-4098-877f-fbec2f1f6947
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSyncOperation::Execute
Exécute de façon synchrone l'exécution et retourne.  
  
## Syntaxe  
  
```  
HRESULT Execute(  
   IUnknown**  ppunkResult  
);  
```  
  
#### Paramètres  
 `ppunkResult`  
 \[out\]  Le paramètre de l'objet retourné par l'exécution.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_ABORT`|L'opération a été interrompue en appelant la méthode d' `IDebugSyncOperation::InProgressAbort` .|  
  
## Notes  
 Process Debug Manager dans le thread cible appelle la méthode d' `Execute` de façon synchrone.  
  
## Voir aussi  
 [IDebugSyncOperation, interface](../../winscript/reference/idebugsyncoperation-interface.md)