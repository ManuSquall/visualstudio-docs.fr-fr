---
title: "IDebugHelper::CreatePropertyBrowser | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugHelper.CreatePropertyBrowser
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugHelper::CreatePropertyBrowser"
ms.assetid: 2fa819cf-c7f7-4bd7-b018-ea33b804ba8f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugHelper::CreatePropertyBrowser
Retourne l'Explorateur de propriétés qui encapsule une VARIANT.  
  
## Syntaxe  
  
```  
HRESULT CreatePropertyBrowser(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugProperty**          ppdob  
);  
```  
  
#### Paramètres  
 `pvar`  
 \[in\]  Variant racine à rechercher.  
  
 `bstrName`  
 \[in\]  Nom pour permettre la racine.  
  
 `pdat`  
 \[in\]  Thread sur lequel pour demander des propriétés.  Si ce paramètre a la valeur NULL, aucun marshaling n'est effectuée.  
  
 `ppdob`  
 \[out\]  Explorateur de propriétés.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode retourne l'Explorateur de propriétés qui encapsule une VARIANT.  
  
## Voir aussi  
 [IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)   
 [IDebugHelper, interface](../../winscript/reference/idebughelper-interface.md)   
 [IDebugProperty, interface](../../winscript/reference/idebugproperty-interface.md)