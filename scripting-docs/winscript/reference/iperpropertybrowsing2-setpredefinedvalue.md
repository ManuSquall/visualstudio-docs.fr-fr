---
title: "IPerPropertyBrowsing2::SetPredefinedValue | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.SetPredefinedValue
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::SetPredefinedValue"
ms.assetid: 3aff5300-c5a4-4d9b-9d47-a75b64014ac4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::SetPredefinedValue
Définit la valeur de la propriété spécifiée par `dispID`.  La valeur prédéfinie est identifiée par `dwCookie.`de jeton  
  
## Syntaxe  
  
```  
HRESULT SetPredefinedValue(  
   DISPID  dispid,  
   DWORD  dwCookie  
);  
```  
  
#### Paramètres  
 `dispid`  
 \[in\]  Acheminez l'identificateur de la propriété pour laquelle une valeur prédéfinie est définie.  
  
 `dwCookie`  
 \[in\]  Jeton identificateur la valeur pour définir.  
  
## Valeur de retour  
 Retourne `HRESULT`valide, en général `S_OK`.  
  
## Voir aussi  
 [IPerPropertyBrowsing2, interface](../../winscript/reference/iperpropertybrowsing2-interface-1.md)