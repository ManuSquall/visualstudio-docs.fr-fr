---
title: "IDebugExtendedProperty::GetExtendedPropertyInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExtendedProperty.GetExtendedPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugExtendedProperty::GetExtendedPropertyInfo"
ms.assetid: 56edf538-5082-4653-82b6-e6640d6f61ba
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExtendedProperty::GetExtendedPropertyInfo
Récupère des informations étendues pour une propriété étendue, qui est plus d'informations que `IDebugProperty`plus simple.  
  
## Syntaxe  
  
```  
HRESULT GetExtendedPropertyInfo(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   ExtendedDebugPropertyInfo*  pExtendedPropertyInfo  
);  
```  
  
#### Paramètres  
 `dwFieldSpec`  
 \[in\]  Spécifie les constantes d'EX\_DBGPROP\_INFO\_FLAGS qui déterminent les champs à remplir la structure d' `ExtendedDebugPropertyInfo` .  
  
 `nRadix`  
 \[in\]  Radis à utiliser en interprétant les informations numériques.  
  
 `pExtendedPropertyInfo`  
 \[out\]  Retourne la structure d' `ExtendedDebugPropertyInfo` qui décrit la propriété.  
  
## Valeur de retour  
 Retourne `HRESULT`valide, en général `S_OK`.  
  
## Voir aussi  
 [IDebugExtendedProperty, interface](../../winscript/reference/idebugextendedproperty-interface.md)   
 [EX\_DBGPROP\_INFO\_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)   
 [ExtendedDebugPropertyInfo, structure](../../winscript/reference/extendeddebugpropertyinfo-structure.md)