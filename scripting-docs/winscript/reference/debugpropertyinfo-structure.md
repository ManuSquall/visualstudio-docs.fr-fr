---
title: Structure DebugPropertyInfo | Microsoft Docs
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
ms.openlocfilehash: 99208626b41f2463178bccecf73c21a1d15fa765
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955261"
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
  
 bstrType  
 Le type de propriété, en tant que chaîne mise en forme.  
  
 bstrValue  
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