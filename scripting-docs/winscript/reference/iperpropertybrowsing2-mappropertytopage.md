---
title: "IPerPropertyBrowsing2::MapPropertyToPage | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.MapPropertyToPage
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::MapPropertyToPage"
ms.assetid: e6418a8e-500b-42e1-9b5a-52e6f7567f99
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::MapPropertyToPage
Retourne le CLSID de la page de propriétés qui peut être utilisée pour modifier cette propriété.  
  
## Syntaxe  
  
```  
HRESULT MapPropertyToPage(  
   DISPID  dispid,  
   CLSID*  pClsidPropPage  
);  
```  
  
#### Paramètres  
 `dispid`  
 \[in\]  Identificateur de dispatch de la propriété concernée.  
  
 `pClsidPropPage`  
 \[out\]  Le pointeur vers le CLSID identificateur la page de propriétés associée à la propriété.  Si cette méthode échoue, \*`pClsidPropPage` a la valeur CLSID\_NULL.  
  
## Valeur de retour  
 Retourne `HRESULT`valide, en général `S_OK`.  
  
## Voir aussi  
 [IPerPropertyBrowsing2, interface](../../winscript/reference/iperpropertybrowsing2-interface-1.md)