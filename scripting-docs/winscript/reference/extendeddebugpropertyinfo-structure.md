---
title: ExtendedDebugPropertyInfo (Structure) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: ee06b0ace93f068e0530a3aa62b8c28d11069f44
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641329"
---
# <a name="extendeddebugpropertyinfo-structure"></a>ExtendedDebugPropertyInfo, structure
Étend la `DebugPropertyInfo` structure avec des membres supplémentaires pour caractériser la propriété étendue.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="members"></a>Membres  
 `dwValidFields`  
 Type de données énuméré permet de spécifier les champs qui sont initialisés.  
  
 `bstrName`  
 Le nom de propriété dans un contexte.  
  
 `bstrType`  
 Le type de propriété en tant que chaîne mise en forme.  
  
 `bstrValue`  
 La valeur de propriété sous forme de chaîne mise en forme.  
  
 `bstrFullName`  
 Le nom complet de la propriété.  
  
 `dwAttrib`  
 Énumération qui spécifie les indicateurs pour les attributs de propriété de débogage.  
  
 `pDebugProp`  
 `IDebugProperty`objet correspondant à cet `ExtendedDebugPropertyInfo`.  
  
 `nDISPID`  
 L’id de dispatch.  
  
 `nType`  
 Le type de propriété étendue.  
  
 `varValue`  
 La valeur de propriété étendue si elle peut être contenue dans la variante.  
  
 `plbValue`  
 Les octets de données réelles de la valeur de propriété.  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty`objet correspondant à cet `ExtendedDebugPropertyInfo`.  
  
## <a name="see-also"></a>Voir aussi  
 [DebugPropertyInfo (Structure)](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty (Interface)](../../winscript/reference/idebugproperty-interface.md)   
 [IDebugExtendedProperty (Interface)](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)