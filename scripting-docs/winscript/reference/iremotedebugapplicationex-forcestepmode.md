---
title: "IRemoteDebugApplicationEx:ForceStepMode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEx:ForceStepMode
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEx:ForceStepMode"
ms.assetid: 83e69a3e-e4c9-4ddd-b01b-1820e4177a03
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplicationEx:ForceStepMode
Force le débogueur en mode en pas \- à \- pas.  
  
## Syntaxe  
  
```  
HRESULT ForceStepMode(  
   IRemoteDebugApplicationThread*  pStepThread  
);  
```  
  
#### Paramètres  
 `pStepThread`  
 \[in\]  Le thread pour le processus de débogage le moniteur pour passer.  Si null, le PDM efface le thread de progression.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
  
## Voir aussi  
 [IRemoteDebugApplicationEx Interface](http://msdn.microsoft.com/fr-fr/2f65fa67-06b7-4053-8945-22383ab66343)