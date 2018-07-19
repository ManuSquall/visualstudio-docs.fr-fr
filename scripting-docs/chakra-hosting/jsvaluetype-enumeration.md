---
title: JsValueType, énumération | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsValueType
helpviewer_keywords:
- JsValueType enumeration
ms.assetid: 6645e723-e554-41fc-b622-ab54ee044b3d
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df4f61cf9118c19a0fc35e7505af422b812d0b43
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569049"
---
# <a name="jsvaluetype-enumeration"></a>JsValueType, énumération
Type JavaScript de JsValueRef.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="members"></a>Membres  
  
### <a name="values"></a>Valeurs  
  
|Nom|Description|  
|----------|-----------------|  
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
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)