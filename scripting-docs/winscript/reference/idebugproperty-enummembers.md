---
title: "IDebugProperty::EnumMembers | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.EnumMembers
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::EnumMembers"
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::EnumMembers
Énumère les membres d'une propriété.  
  
## Syntaxe  
  
```  
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGS dwFieldSpec,  
   UINT nRadix,  
   REFIID refiid,  
   IEnumDebugPropertyInfo** ppEnum  
);  
```  
  
#### Paramètres  
 `dwFieldSpec`  
 \[in\]  Spécifie les constantes d' `DBGPROP_INFO_FLAGS` qui déterminent quels champs dans l'énumération debug des structures de propriété doivent être remplis.  
  
 `nRadix`  
 \[in\]  Radis à utiliser en interprétant les informations numériques.  
  
 `refiid`  
 \[in\]  Cet IID est passée pour filtrer l'énumérateur.  L'IID est l'une des interfaces d' `IDebugPropertyEnumType` qui héritent d' `IDebugPropertyEnumType_All`.  
  
 `ppEnum`  
 \[out\]  Retourne l'interface d' `IEnumDebugPropertyInfo` qui énumère les propriétés du membre.  
  
## Valeur de retour  
 Retourne `HRESULT`valide, en général `S_OK`.  
  
## Voir aussi  
 [IDebugProperty, interface](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [IDebugPropertyEnumType\_All, interface](../../winscript/reference/idebugpropertyenumtype-all-interface.md)   
 [IEnumDebugPropertyInfo, interface](../../winscript/reference/ienumdebugpropertyinfo-interface.md)