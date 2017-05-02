---
title: "IDebugFormatter::GetVariantForString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugFormatter.GetVariantForString
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugFormatter::GetVariantForString"
ms.assetid: 2993431d-0ee2-4d8d-b62c-0a810a8bc391
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugFormatter::GetVariantForString
Retourne une VARIANT contenant la chaîne spécifiée.  
  
## Syntaxe  
  
```  
HRESULT GetVariantForString(  
   LPCOLESTR  pwstrValue,  
   VARIANT*   pvar  
);  
```  
  
#### Paramètres  
 `pwstrValue`  
 \[in\]  Chaîne à stocker dans une VARIANT.  
  
 `pvar`  
 \[out\]  `pwstrValue`contenant VARIANT.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode retourne une VARIANT contenant la chaîne spécifiée.  
  
## Voir aussi  
 [IDebugFormatter, interface](../../winscript/reference/idebugformatter-interface.md)