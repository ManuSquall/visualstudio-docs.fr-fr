---
title: IDebugProperty::GetPropertyInfo | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetPropertyInfo
ms.assetid: b201c0c4-bff6-4285-880f-67be90584c5f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: edd878419c6f2b4fd0f882a070d80c98a96eba56
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727669"
---
# <a name="idebugpropertygetpropertyinfo"></a>IDebugProperty::GetPropertyInfo
Obtient la valeur d’une `IDebugProperty` qui décrit une méthode ou une propriété indexée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetPropertyInfo (  
   DBGPROP_INFO_FLAGSdwFields,  
   UINT nRadix,  
   DebugPropertyInfo* pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwFields`  
 [in] Spécifie le `DBGPROP_INFO_FLAGS` constantes qui déterminent les champs à être rempli le `DebugPropertyInfo` structure.  
  
 `nRadix`  
 [in] Base à utiliser dans toutes les informations numériques de mise en forme.  
  
 `pPropertyInfo`  
 [out] Retourne le `DebugPropertyInfo` structure qui décrit la propriété.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un élément valide `HRESULT`, généralement `S_OK`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProperty (Interface)](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [Structure DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)