---
title: "IDebugProperty::GetPropertyInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.GetPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::GetPropertyInfo"
ms.assetid: b201c0c4-bff6-4285-880f-67be90584c5f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::GetPropertyInfo
Obtient la valeur d' `IDebugProperty` qui décrit une méthode ou une propriété indexée.  
  
## Syntaxe  
  
```  
HRESULT GetPropertyInfo (  
   DBGPROP_INFO_FLAGS dwFields,  
   UINT nRadix,  
   DebugPropertyInfo* pPropertyInfo  
);  
```  
  
#### Paramètres  
 `dwFields`  
 \[in\]  Spécifie les constantes d' `DBGPROP_INFO_FLAGS` qui déterminent les champs à remplir la structure d' `DebugPropertyInfo` .  
  
 `nRadix`  
 \[in\]  Radis à utiliser lors de la mise en forme les informations numériques.  
  
 `pPropertyInfo`  
 \[out\]  Retourne la structure d' `DebugPropertyInfo` qui décrit la propriété.  
  
## Valeur de retour  
 Retourne `HRESULT`valide, en général `S_OK`.  
  
## Voir aussi  
 [IDebugProperty, interface](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [DebugPropertyInfo, structure](../../winscript/reference/debugpropertyinfo-structure.md)