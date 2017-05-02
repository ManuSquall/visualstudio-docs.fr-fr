---
title: "IRemoteDebugApplication::CauseBreak | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.CauseBreak
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::CauseBreak"
ms.assetid: 6a2c27bb-dca0-475c-9918-bdbb70a50d26
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IRemoteDebugApplication::CauseBreak
Entraîne l'application pour arrêter le plus tôt possible.  
  
## Syntaxe  
  
```  
HRESULT CauseBreak();  
```  
  
#### Paramètres  
 Cette méthode n'accepte pas de paramètres.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Appeler cette méthode ne provoque pas une application de s'arrêter immédiatement.  Si l'application n'est pas actuellement code de script, longtemps peut s'écouler avant que l'application s'arrête réellement.  
  
## Voir aussi  
 [IRemoteDebugApplication, interface](../../winscript/reference/iremotedebugapplication-interface.md)