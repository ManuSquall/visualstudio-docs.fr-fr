---
title: "IDebugHelper::CreateSimpleConnectionPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugHelper.CreateSimpleConnectionPoint
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugHelper::CreateSimpleConnectionPoint"
ms.assetid: 5e4798ce-6f9f-4184-9853-67bf8c8524ab
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugHelper::CreateSimpleConnectionPoint
Retourne une interface d'événement qui encapsule un objet donné d' `IDispatch` .  
  
## Syntaxe  
  
```  
HRESULT CreateSimpleConnectionPoint(  
   IDispatch*                pdisp   
   ISimpleConnectionPoint**  ppscp  
);  
```  
  
#### Paramètres  
 `pdisp`  
 \[in\]  l'objet d' `IDispatch` à l'enveloppe.  
  
 `ppscp`  
 \[out\]  l'interface d'événement qui encapsule `pdisp`.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Retourne une interface d'événement qui encapsule `IDispatch` donné \(voir l' [ISimpleConnectionPoint, interface](../../winscript/reference/isimpleconnectionpoint-interface.md)\).  
  
## Voir aussi  
 [IDebugHelper, interface](../../winscript/reference/idebughelper-interface.md)   
 [ISimpleConnectionPoint, interface](../../winscript/reference/isimpleconnectionpoint-interface.md)