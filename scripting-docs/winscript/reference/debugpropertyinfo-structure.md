---
title: "DebugPropertyInfo, structure | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DebugPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DebugPropertyInfo (structure)"
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DebugPropertyInfo, structure
Décrit un objet d'une nature hiérarchique avec le nom, le type, et la valeur.  Elle est utilisée pour décrire les propriétés de débogage des variables locales, les paramètres, les variables et les expressions de l'indique, et les registres.  
  
## Syntaxe  
  
```  
typedef struct DebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   BSTR  bstrName;  
   BSTR  bstrType;  
   BSTR  bstrValue;  
   BSTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
};  
```  
  
## Membres  
 dwValidFields  
 Un type de données énuméré utilisé pour spécifier les champs qui sont initialisés.  
  
 bstrName  
 Le nom de la propriété dans un contexte.  
  
 bstrType  
 Le type de propriété, en tant que chaîne mise en forme.  
  
 bstrValue  
 La valeur de propriété, en tant que chaîne mise en forme.  
  
 bstrFullName  
 Le nom complet de la propriété.  
  
 dwAttrib  
 Énumération qui spécifie des indicateurs pour la propriété de débogage l'attribut.  
  
 pDebugProp  
 `IDebugProperty` décrit par les informations dans cette structure d' `DebugPropertyInfo` .  
  
## Voir aussi  
 [IDebugProperty, interface](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP\_ATTRIB\_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)