---
title: "IRemoteDebugApplicationEvents::OnSetName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEvents.OnSetName
apilocation: jscript.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEvents::OnSetName"
ms.assetid: 524dcff3-fb48-4d8f-8989-73eb539454fb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationEvents::OnSetName
Gère un événement de nom défini.  
  
## Syntaxe  
  
```  
HRESULT OnSetName(  
   LPCOLESTR  pstrName  
);  
```  
  
#### Paramètres  
 `pstrName`  
 \[in\] Nouveau nom.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode gère un événement de nom défini.  
  
## Voir aussi  
 [IRemoteDebugApplicationEvents, interface](../../winscript/reference/iremotedebugapplicationevents-interface.md)