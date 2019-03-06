---
title: Structure DebugPropertyInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 47c0f6a359341d19b99c1ce8c099ebf1c6d6a1ff
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088983"
---
# <a name="debugpropertyinfo-structure"></a>DebugPropertyInfo, structure
Décrit un objet de nature hiérarchique qui a le nom, type et valeur. Il est utilisé pour décrire les propriétés de débogage de variables locales, des paramètres, des variables espionnes et des expressions et inscrit.  
  
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
 Type de données énuméré permet de spécifier quels champs sont initialisés.  
  
 bstrName  
 Le nom de propriété dans un contexte.  
  
 bstrType argument de type  
 Le type de propriété, en tant que chaîne mise en forme.  
  
 bstrValue Argument de type  
 La valeur de propriété en tant que chaîne mise en forme.  
  
 bstrFullName  
 Le nom complet de la propriété.  
  
 dwAttrib  
 Énumération qui spécifie les indicateurs pour les attributs de propriété de débogage.  
  
 pDebugProp  
 Le `IDebugProperty` décrite par les informations contenues dans cette `DebugPropertyInfo` structure.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProperty (Interface)](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)