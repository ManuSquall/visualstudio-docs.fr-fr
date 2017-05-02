---
title: "IDebugHelper::CreatePropertyBrowserEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugHelper.CreatePropertyBrowserEx
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugHelper::CreatePropertyBrowserEx"
ms.assetid: 87ad322f-09da-4ce8-bb68-0b0bbeec645b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugHelper::CreatePropertyBrowserEx
Retourne l'Explorateur de propriétés qui encapsule une VARIANT et permet de la conversion personnalisée des valeurs VARIANTES ou des types de VARTYPE aux chaînes.  
  
## Syntaxe  
  
```  
HRESULT CreatePropertyBrowserEx(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugFormatter*          pdf,  
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
  
 `pdf`  
 \[in\]  Objet qui fournit la mise en forme personnalisée pour les variantes.  
  
 `ppdob`  
 \[out\]  Explorateur de propriétés.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode retourne l'Explorateur de propriétés qui encapsule une VARIANT et permet de la conversion personnalisée des valeurs VARIANTES ou des types de VARTYPE aux chaînes.  
  
## Voir aussi  
 [IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)   
 [IDebugHelper, interface](../../winscript/reference/idebughelper-interface.md)   
 [IDebugProperty, interface](../../winscript/reference/idebugproperty-interface.md)