---
title: "ExtendedDebugPropertyInfo, structure | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ExtendedDebugPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ExtendedDebugPropertyInfo (structure)"
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ExtendedDebugPropertyInfo, structure
Étend la structure d' `DebugPropertyInfo` avec les membres supplémentaires pour caractériser la propriété étendue.  
  
## Syntaxe  
  
```  
typedef struct ExtendedDebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   LPOLESTR  bstrName;  
   LPOLESTR  bstrType;  
   LPOLESTR  bstrValue;  
   LPOLESTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
   DWORD  nDISPID;  
   DWORD  nType;  
   VARIANT  varValue;  
   ILockBytes*  plbValue;  
   IDebugExtendedProperty*  pDebugExtProp;  
};  
```  
  
## Membres  
 `dwValidFields`  
 Un type de données énuméré utilisé pour spécifier les champs qui sont initialisés.  
  
 `bstrName`  
 Le nom de la propriété dans un contexte.  
  
 `bstrType`  
 Le type de propriété comme chaîne mise en forme.  
  
 `bstrValue`  
 La valeur de propriété comme une chaîne mise en forme.  
  
 `bstrFullName`  
 Le nom complet de la propriété.  
  
 `dwAttrib`  
 Énumération qui spécifie des indicateurs pour la propriété de débogage l'attribut.  
  
 `pDebugProp`  
 Objet d'`IDebugProperty` correspondant à cet `ExtendedDebugPropertyInfo`.  
  
 `nDISPID`  
 L'ID d'expédition  
  
 `nType`  
 Le type de propriété étendue.  
  
 `varValue`  
 La valeur de propriété étendue si elle peut tenir dans la VARIANT.  
  
 `plbValue`  
 Les octets de données réels de la valeur de propriété.  
  
 `pDebugExtProp`  
 Objet d'`IDebugExtendedProperty` correspondant à cet `ExtendedDebugPropertyInfo`.  
  
## Voir aussi  
 [DebugPropertyInfo, structure](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty, interface](../../winscript/reference/idebugproperty-interface.md)   
 [IDebugExtendedProperty, interface](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP\_ATTRIB\_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)