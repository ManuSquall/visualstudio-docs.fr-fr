---
title: "IRemoteDebugApplicationEvents::OnConnectDebugger | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEvents.OnConnectDebugger
apilocation: jscript.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEvents::OnConnectDebugger"
ms.assetid: 8c9c19b8-5426-4643-83e6-b68803ff69c4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationEvents::OnConnectDebugger
Gère un débogueur connectent l'événement.  
  
## Syntaxe  
  
```  
HRESULT OnConnectDebugger(  
   IApplicationDebugger*  pad  
);  
```  
  
#### Paramètres  
 `pad`  
 \[in\]  Le débogueur récemment connecté.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode gère le débogueur connectent l'événement.  
  
## Voir aussi  
 [IRemoteDebugApplicationEvents, interface](../../winscript/reference/iremotedebugapplicationevents-interface.md)