---
title: Énumération JS_PROPERTY_ATTRIBUTES | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JS_PROPERTY_ATTRIBUTES
apilocation:
- jscript9diag.dll
ms.assetid: e83b9b6c-5b21-48d1-92b6-22bed926b18b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed034ef6fc134838058b75534f1b5c17c1ec2e3d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24733769"
---
# <a name="jspropertyattributes-enumeration"></a>Énumération JS_PROPERTY_ATTRIBUTES
Indique les attributs d'une propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
enum JS_PROPERTY_ATTRIBUTES{   JS_PROPERTY_ATTRIBUTE_NONE = 0,   JS_PROPERTY_HAS_CHILDREN = 0x1,   JS_PROPERTY_FAKE = 0x2,   JS_PROPERTY_METHOD = 0x4,   JS_PROPERTY_READONLY = 0x8,   JS_PROPERTY_NATIVE_WINRT_POINTER = 0x10} JS_PROPERTY_ATTRIBUTES;  
```  
  
## <a name="members"></a>Membres  
  
|Nom|Description|  
|----------|-----------------|  
|`JS_PROPERTY_ATTRIBUTE_NONE`|La propriété n’a pas d’attributs.|  
|`JS_PROPERTY_HAS_CHILDREN`|La propriété a des enfants.|  
|`JS_PROPERTY_FAKE`|La propriété représente un nœud fictif, tels que « [méthodes] ».|  
|`JS_PROPERTY_METHOD`|La propriété est une méthode.|  
|`JS_PROPERTY_READONLY`|La propriété doit être en lecture seule.|  
|`JS_PROPERTY_NATIVE_WINRT_POINTER`|La propriété est un pointeur vers un objet WinRT natif.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence d’interfaces de script Windows](../../winscript/reference/windows-script-interfaces-reference.md)