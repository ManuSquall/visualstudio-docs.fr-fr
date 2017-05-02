---
title: "IDebugProperty::SetValueAsString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.SetValueAsString
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::SetValueAsString"
ms.assetid: cad8d7b2-19a5-4a29-9000-cafdecdc238b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::SetValueAsString
Définit la valeur d'une propriété d'une chaîne donnée.  
  
## Syntaxe  
  
```  
HRESULT SetValueAsString (  
   LPCOLESTR pszValue,  
   UINT nRadix,  
);  
```  
  
#### Paramètres  
 `pszValue`  
 \[in\]  La valeur à définir.  
  
 `nRadix`  
 \[in\]  Radis à utiliser en interprétant les informations numériques.  
  
## Valeur de retour  
 Retourne `HRESULT`valide, en général `S_OK`.  
  
## Voir aussi  
 [IDebugProperty, interface](../../winscript/reference/idebugproperty-interface.md)