---
title: ExtendedDebugPropertyInfo Structure | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ExtendedDebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- ExtendedDebugPropertyInfo structure
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1fe0eef00d2bf064a8a002925f4ba5607d36f31c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955180"
---
# <a name="extendeddebugpropertyinfo-structure"></a>ExtendedDebugPropertyInfo, structure
Étend la `DebugPropertyInfo` structure avec des membres supplémentaires pour caractériser la propriété étendue.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
  
## <a name="members"></a>Membres  
 `dwValidFields`  
 Type de données énuméré permet de spécifier quels champs sont initialisés.  
  
 `bstrName`  
 Le nom de propriété dans un contexte.  
  
 `bstrType`  
 Le type de propriété en tant que chaîne mise en forme.  
  
 `bstrValue`  
 La valeur de propriété sous forme de chaîne.  
  
 `bstrFullName`  
 Le nom complet de la propriété.  
  
 `dwAttrib`  
 Énumération qui spécifie les indicateurs pour les attributs de propriété de débogage.  
  
 `pDebugProp`  
 `IDebugProperty` objet correspondant à cet `ExtendedDebugPropertyInfo`.  
  
 `nDISPID`  
 L’id de dispatch.  
  
 `nType`  
 Le type de propriété étendue.  
  
 `varValue`  
 La valeur de propriété étendue si elle peut tenir dans la variante.  
  
 `plbValue`  
 Les octets de données réelles de la valeur de propriété.  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty` objet correspondant à cet `ExtendedDebugPropertyInfo`.  
  
## <a name="see-also"></a>Voir aussi  
 [DebugPropertyInfo (Structure)](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty (Interface)](../../winscript/reference/idebugproperty-interface.md)   
 [IDebugExtendedProperty (Interface)](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)