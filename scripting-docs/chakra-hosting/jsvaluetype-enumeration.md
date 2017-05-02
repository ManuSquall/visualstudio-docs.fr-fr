---
title: "JsValueType, &#233;num&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsValueType"
helpviewer_keywords: 
  - "JsValueType (énumération)"
ms.assetid: 6645e723-e554-41fc-b622-ab54ee044b3d
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# JsValueType, &#233;num&#233;ration
Type JavaScript de JsValueRef.  
  
## Syntaxe  
  
```  
enum JsValueType {  
    JsUndefined      = 0,  
    JsNull           = 1,  
    JsNumber         = 2,  
    JsString         = 3,  
    JsBoolean        = 4,  
    JsObject         = 5,  
    JsFunction       = 6,  
    JsError          = 7,  
    JsArray          = 8,  
    JsSymbol         = 9,  
    JsArrayBuffer    = 10,  
    JsTypedArray     = 11,  
    JsDataView       = 12,  
};  
```  
  
## Membres  
  
### Valeurs  
  
|Nom|Description|  
|---------|-----------------|  
|`JsUndefined`|La valeur est `undefined`.|  
|`JsNull`|La valeur est `null`.|  
|`JsNumber`|La valeur est un nombre JavaScript.|  
|`JsString`|La valeur est une chaîne JavaScript.|  
|`JsBoolean`|La valeur est une valeur JavaScript booléenne.|  
|`JsObject`|La valeur est un objet JavaScript.|  
|`JsFunction`|La valeur est un objet de fonction JavaScript.|  
|`JsError`|La valeur est un objet d'erreur JavaScript.|  
|`JsArray`|La valeur est un objet de tableau JavaScript.|  
|`JsSymbol`|La valeur est un symbole JavaScript.<br /><br /> Cette valeur d'énumération est prise en charge uniquement dans le mode Edge.|  
|`JsArrayBuffer`|La valeur est un objet `ArrayBuffer` JavaScript.<br /><br /> Cette valeur d'énumération est prise en charge uniquement dans le mode Edge.|  
|`JsTypedArray`|La valeur est un objet de tableau typé JavaScript.<br /><br /> Cette valeur d'énumération est prise en charge uniquement dans le mode Edge.|  
|`JsDataView`|La valeur est un objet `DataView` JavaScript.<br /><br /> Cette valeur d'énumération est prise en charge uniquement dans le mode Edge.|  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)