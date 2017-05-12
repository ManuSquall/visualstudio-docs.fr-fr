---
title: "IDebugExtendedProperty::EnumExtendedMembers | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExtendedProperty.EnumExtendedMembers
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugExtendedProperty::EnumExtendedMembers"
ms.assetid: 27cdb091-da4e-44d2-a631-31ae00468b98
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExtendedProperty::EnumExtendedMembers
Énumère les membres d'une propriété étendue.  
  
## Syntaxe  
  
```  
HRESULT EnumExtendedMembers(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   IEnumDebugExtendedPropertyInfo**  ppeepi  
);  
```  
  
#### Paramètres  
 `dwFieldSpec`  
 \[in\]  Spécifie les constantes d'EX\_DBGPROP\_INFO\_FLAGS qui déterminent les champs de l'étendue énuméré debug des structures de propriété qui doivent être remplies.  
  
 `nRadix`  
 \[in\]  Radis à utiliser en interprétant les informations numériques.  
  
 `ppeepi`  
 \[out\]  Retourne l'interface d' `IEnumDebugExtendedPropertyInfo` qui énumère les propriétés du membre.  
  
## Valeur de retour  
 Retourne `HRESULT`valide, en général `S_OK`.  
  
## Voir aussi  
 [IDebugExtendedProperty, interface](../../winscript/reference/idebugextendedproperty-interface.md)   
 [EX\_DBGPROP\_INFO\_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)   
 [ExtendedDebugPropertyInfo, structure](../../winscript/reference/extendeddebugpropertyinfo-structure.md)