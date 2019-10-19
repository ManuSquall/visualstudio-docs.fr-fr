---
title: ExtendedDebugPropertyInfo, structure | Microsoft Docs
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
ms.openlocfilehash: 09f3c5a219fca9ec9b881e2ae8363aae4d48e03f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575833"
---
# <a name="extendeddebugpropertyinfo-structure"></a>ExtendedDebugPropertyInfo, structure
Étend la structure `DebugPropertyInfo` avec des membres supplémentaires pour caractériser la propriété étendue.  
  
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
 Type de données énuméré utilisé pour spécifier les champs à initialiser.  
  
 `bstrName`  
 Nom de la propriété dans un contexte.  
  
 `bstrType`  
 Type de propriété comme chaîne mise en forme.  
  
 `bstrValue`  
 Valeur de la propriété sous la forme d’une chaîne mise en forme.  
  
 `bstrFullName`  
 Nom complet de la propriété.  
  
 `dwAttrib`  
 Énumération qui spécifie les indicateurs pour les attributs de propriété de débogage.  
  
 `pDebugProp`  
 `IDebugProperty` objet correspondant à cet `ExtendedDebugPropertyInfo`.  
  
 `nDISPID`  
 ID de dispatch.  
  
 `nType`  
 Type de propriété étendue.  
  
 `varValue`  
 Valeur de la propriété étendue si elle peut tenir dans une variante.  
  
 `plbValue`  
 Octets de données réels de la valeur de propriété.  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty` objet correspondant à cet `ExtendedDebugPropertyInfo`.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de la [structure DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)  
 @No__t_1 de l' [interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)  
 @No__t_1 de l' [interface IDebugExtendedProperty](../../winscript/reference/idebugextendedproperty-interface.md)  
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)    
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)