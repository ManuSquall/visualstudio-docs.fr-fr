---
title: "DBGPROP_INFO_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DBGPROP_INFO_FLAGS
apilocation: scrobj.dll
f1_keywords: 
  - "DBGPROP_INFO_FLAGS"
helpviewer_keywords: 
  - "DBGPROP_INFO_FLAGS"
ms.assetid: e9450a21-a802-4c3e-8b3d-8e202f555de1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DBGPROP_INFO_FLAGS
Utilisé pour spécifier les champs d' `DebugPropertyInfo`  
  
## Syntaxe  
  
```  
enum {  
   DBGPROP_INFO_NAME  =0x001,  
   DBGPROP_INFO_TYPE  =0x002,  
   DBGPROP_INFO_VALUE  =0x004,  
   DBGPROP_INFO_FULLNAME  =0x020,  
   DBGPROP_INFO_ATTRIBUTES  =0x008,  
   DBGPROP_INFO_DEBUGPROP  =0x010,  
   DBGPROP_INFO_AUTOEXPAND  =0x8000000  
};  
```  
  
## Membres  
 DBGPROP\_INFORMATION\_NAME  
 Initialise le champ d' `bstrName` .  
  
 DBGPROP\_INFORMATION\_TYPE  
 Initialise le champ d' `bstrType` .  
  
 DBGPROP\_INFORMATION\_VALUE  
 Initialise le champ d' `bstrValue` .  
  
 DBGPROP\_INFORMATION\_FULLNAME  
 Initialise le champ d' `bstrFullName` .  
  
 DBGPROP\_INFORMATION\_ATTRIBUTES  
 Initialise le champ d' `dwAttrib` .  
  
 DBGPROP\_INFORMATION\_DEBUGPROP  
 Initialise le champ d' `pDebugProp` qui contient une interface d' `IDebugProperty` .  
  
 DBGPROP\_INFORMATION\_AUTOEXPAND  
 Spécifie que le champ de valeur doit contenir la valeur automatique développée, si disponible, pour ce type d'objet.  
  
## Voir aussi  
 [DebugPropertyInfo, structure](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty, interface](../../winscript/reference/idebugproperty-interface.md)