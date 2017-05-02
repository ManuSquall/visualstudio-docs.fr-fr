---
title: "IRemoteDebugApplicationEvents::OnBreakFlagChange | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEvents.OnBreakFlagChange
apilocation: jscript.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEvents::OnBreakFlagChange"
ms.assetid: 25684454-a0d8-47e0-85f5-2217069a9f45
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationEvents::OnBreakFlagChange
Gère un événement lorsque des balises d'arrêt sont modifiées.  
  
## Syntaxe  
  
```  
HRESULT OnBreakFlagChange(  
   APPBREAKFLAGS                   abf,  
   IRemoteDebugApplicationThread*  prdatSteppingThread  
);  
```  
  
#### Paramètres  
 `abf`  
 \[in\]  Les balises actuelles de l'arrêt de l'application.  
  
 `prdatSteppingThread`  
 \[in\]  Le thread en cours de exécution.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode gère l'événement lorsque la modification des balises de saut de ligne.  
  
## Voir aussi  
 [IRemoteDebugApplicationEvents, interface](../../winscript/reference/iremotedebugapplicationevents-interface.md)   
 [APPBREAKFLAGS, énumération](../../winscript/reference/appbreakflags-enumeration.md)