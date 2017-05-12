---
title: "Structure JsDebugPropertyInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JsDebugPropertyInfo
apilocation: jscript9diag.dll
ms.assetid: 3a5463a7-2013-4846-9ab2-8beb675a5a6a
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Structure JsDebugPropertyInfo
Indique des informations sur une propriété.  
  
## Syntaxe  
  
```  
typedef struct tagJsDebugPropertyInfo  
{  
   BSTR name;  
   BSTR type;  
   BSTR value;  
   BSTR fullName;  
   JS_PROPERTY_ATTRIBUTES attr;  
} JsDebugPropertyInfo;  
```  
  
## Membres  
 `name`  
 le nom de la propriété ;  
  
 `type`  
 Type de la propriété.  
  
 `value`  
 Valeur de la propriété.  
  
 `fullName`  
 Nom complet de la propriété.  
  
 `attr`  
 Énumération qui représente la propriété les attributs.  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [Interfaces Windows Script, référence](../../winscript/reference/windows-script-interfaces-reference.md)