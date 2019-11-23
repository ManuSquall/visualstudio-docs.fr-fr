---
title: DebugPropertyInfo, structure | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugPropertyInfo structure
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 793c83b467460f0744abffe3f161f7510f56257a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575065"
---
# <a name="debugpropertyinfo-structure"></a>DebugPropertyInfo, structure
Décrit un objet d’une nature hiérarchique qui a le nom, le type et la valeur. Il est utilisé pour décrire les propriétés de débogage des variables locales, des paramètres, des variables et des expressions espionnes et des registres.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
  
## <a name="members"></a>Membres  
 dwValidFields  
 Type de données énuméré utilisé pour spécifier les champs à initialiser.  
  
 bstrName,  
 Nom de la propriété dans un contexte.  
  
 bstrType  
 Type de propriété, comme chaîne mise en forme.  
  
 bstrValue  
 Valeur de la propriété, comme chaîne mise en forme.  
  
 bstrFullName  
 Nom complet de la propriété.  
  
 dwAttrib  
 Énumération qui spécifie les indicateurs pour les attributs de propriété de débogage.  
  
 pDebugProp  
 La `IDebugProperty` décrite par les informations de cette structure de `DebugPropertyInfo`.  
  
## <a name="see-also"></a>Voir aussi  
   de l' [interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)  
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)