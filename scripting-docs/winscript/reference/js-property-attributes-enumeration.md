---
title: "&#201;num&#233;ration JS_PROPERTY_ATTRIBUTES | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JS_PROPERTY_ATTRIBUTES
apilocation: jscript9diag.dll
ms.assetid: e83b9b6c-5b21-48d1-92b6-22bed926b18b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# &#201;num&#233;ration JS_PROPERTY_ATTRIBUTES
Indique les attributs d'une propriété.  
  
## Syntaxe  
  
```  
enum JS_PROPERTY_ATTRIBUTES  
{  
   JS_PROPERTY_ATTRIBUTE_NONE = 0,  
   JS_PROPERTY_HAS_CHILDREN = 0x1,  
   JS_PROPERTY_FAKE = 0x2,  
   JS_PROPERTY_METHOD = 0x4,  
   JS_PROPERTY_READONLY = 0x8,  
   JS_PROPERTY_NATIVE_WINRT_POINTER = 0x10  
} JS_PROPERTY_ATTRIBUTES;  
```  
  
## Membres  
  
|Nom|Description|  
|---------|-----------------|  
|`JS_PROPERTY_ATTRIBUTE_NONE`|La propriété n'a aucun attribut.|  
|`JS_PROPERTY_HAS_CHILDREN`|La propriété possède des enfants.|  
|`JS_PROPERTY_FAKE`|La propriété représente un faux nœud, comme « \[des méthodes\] ».|  
|`JS_PROPERTY_METHOD`|La propriété est une méthode.|  
|`JS_PROPERTY_READONLY`|La propriété est en lecture seule.|  
|`JS_PROPERTY_NATIVE_WINRT_POINTER`|La propriété est un pointeur vers un objet natif de WinRT.|  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [Interfaces Windows Script, référence](../../winscript/reference/windows-script-interfaces-reference.md)