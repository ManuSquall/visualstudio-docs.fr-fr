---
title: "IEnumRemoteDebugApplicationThreads::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumRemoteDebugApplicationThreads.Reset
apilocation: pdm.dll
helpviewer_keywords: 
  - "IEnumRemoteDebugApplicationThreads::Reset"
ms.assetid: a6ad8a01-4cc0-4f9c-9cfe-c7448c753473
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumRemoteDebugApplicationThreads::Reset
Réinitialise une séquence d'énumération.  
  
## Syntaxe  
  
```  
HRESULT Reset();  
```  
  
#### Paramètres  
 Cette méthode n'accepte pas de paramètres.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode réinitialise une séquence d'énumération au début.  
  
## Voir aussi  
 [IEnumRemoteDebugApplicationThreads, interface](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)