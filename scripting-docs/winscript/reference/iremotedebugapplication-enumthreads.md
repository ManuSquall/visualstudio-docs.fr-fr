---
title: "IRemoteDebugApplication::EnumThreads | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.EnumThreads
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::EnumThreads"
ms.assetid: b4d7294c-1f15-4f7e-bdfd-700e3bf98cea
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::EnumThreads
Énumère tous les threads connus pour être associé à l'application.  
  
## Syntaxe  
  
```  
HRESULT EnumThreads(  
   IEnumRemoteDebugApplicationThreads**  pperdat  
);  
```  
  
#### Paramètres  
 `pperdat`  
 \[out\]  Énumérateur qui répertorie tous les threads connus pour être associé à l'application.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode énumère tous les threads connus pour être associé à l'application.  De nouveaux threads peuvent être ajoutés à tout moment.  
  
## Voir aussi  
 [IRemoteDebugApplication, interface](../../winscript/reference/iremotedebugapplication-interface.md)