---
title: "IEnumDebugStackFrames::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugStackFrames.Clone
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugStackFrames::Clone"
ms.assetid: 9d9e01a3-0be3-4336-832a-f065af388571
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugStackFrames::Clone
Crée un énumérateur qui contient le même état que l'énumérateur en cours.  
  
## Syntaxe  
  
```  
HRESULT Clone(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### Paramètres  
 `ppedsf`  
 \[out\]  Retourne l'interface d' `IEnumDebugStackFrames`de clone de l'énumérateur.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode crée un énumérateur qui contient le même état que l'énumérateur actuel.  
  
## Voir aussi  
 [IEnumDebugStackFrames, interface](../../winscript/reference/ienumdebugstackframes-interface.md)