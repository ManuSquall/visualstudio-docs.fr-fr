---
title: "IDebugSyncOperation::InProgressAbort | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSyncOperation.InProgressAbort
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugSyncOperation::InProgressAbort"
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSyncOperation::InProgressAbort
Annule une exécution en cours sur un autre thread.  
  
## Syntaxe  
  
```  
HRESULT InProgressAbort();  
```  
  
#### Paramètres  
 Cette méthode n'accepte pas de paramètres.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_NOTIMPL`|L'opération ne peut pas être annulée.|  
|`E_ABORT`|Impossible de terminer l'opération.|  
  
## Notes  
 Process Debug Manager appelle cette méthode du thread du débogueur pour annuler une opération en cours dans un autre thread.  
  
 Si la méthode d' `InProgressAbort` ne peut pas effectuer l'exécution, elle retourne `E_ABORT` dès que possible.  Cette méthode peut retourner `E_NOTIMPL` si l'opération ne peut pas être annulée.  
  
## Voir aussi  
 [IDebugSyncOperation, interface](../../winscript/reference/idebugsyncoperation-interface.md)