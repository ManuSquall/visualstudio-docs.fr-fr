---
title: "IDebugApplication::QueryCurrentThreadIsDebuggerThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.QueryCurrentThreadIsDebuggerThread
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::QueryCurrentThreadIsDebuggerThread"
ms.assetid: e22ad8a4-a8be-423d-80f2-28256a7448ed
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::QueryCurrentThreadIsDebuggerThread
Détermine si le thread en cours de exécution est le thread du débogueur.  
  
## Syntaxe  
  
```  
HRESULT QueryCurrentThreadIsDebuggerThread();  
```  
  
#### Paramètres  
 Cette méthode n'accepte pas de paramètres.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi et le thread en cours de exécution est le thread du débogueur.|  
|`S_FALSE`|Le thread en cours de exécution n'est pas le thread du débogueur.|  
  
## Notes  
 Cette méthode détermine si le thread en cours de exécution est le thread du débogueur.  
  
## Voir aussi  
 [IDebugApplication, interface](../../winscript/reference/idebugapplication-interface.md)