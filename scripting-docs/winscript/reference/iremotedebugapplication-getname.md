---
title: "IRemoteDebugApplication::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.GetName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::GetName"
ms.assetid: 3a8e8a4b-d7d4-40e5-97a1-f6d18db2e9c4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::GetName
Retourne le nom de ce nœud d'application.  
  
## Syntaxe  
  
```  
HRESULT GetName(  
   BSTR*  pbstrName  
);  
```  
  
#### Paramètres  
 `pbstrName`  
 \[out\]  Nom de ce nœud d'application.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode retourne le nom de ce nœud d'application.  
  
## Voir aussi  
 [IRemoteDebugApplication, interface](../../winscript/reference/iremotedebugapplication-interface.md)