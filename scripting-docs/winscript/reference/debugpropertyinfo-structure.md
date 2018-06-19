---
title: DebugPropertyInfo (Structure) | Documents Microsoft
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
ms.openlocfilehash: c9baade1a742a06c952906c05c574e752806bc9c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640809"
---
# <a name="debugpropertyinfo-structure"></a>DebugPropertyInfo, structure
Décrit un objet de nature hiérarchique qui a le nom, type et valeur. Il est utilisé pour décrire les propriétés de débogage des variables locales, des paramètres, des variables espionnes et des expressions et inscrit.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 Type de données énuméré permet de spécifier les champs qui sont initialisés.  
  
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