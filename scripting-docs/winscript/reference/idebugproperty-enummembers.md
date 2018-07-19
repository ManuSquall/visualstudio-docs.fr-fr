---
title: IDebugProperty::EnumMembers | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.EnumMembers
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::EnumMembers
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9cb57f2609fcd9a80e2a9e0dfd63637e6f700047
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727539"
---
# <a name="idebugpropertyenummembers"></a>IDebugProperty::EnumMembers
Énumère les membres d’une propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGSdwFieldSpec,  
   UINTnRadix,  
   REFIIDrefiid,  
   IEnumDebugPropertyInfo**ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwFieldSpec`  
 [in] Spécifie le `DBGPROP_INFO_FLAGS` constantes qui déterminent les champs dans les structures de propriété énumérée de débogage doit être renseigné.  
  
 `nRadix`  
 [in] Base à utiliser pour l’interprétation des informations numériques.  
  
 `refiid`  
 [in] Cet IID est passé pour le filtrage de l’énumérateur. IID fait partie de la `IDebugPropertyEnumType` les interfaces qui héritent de `IDebugPropertyEnumType_All`.  
  
 `ppEnum`  
 [out] Retourne le `IEnumDebugPropertyInfo` interface qui énumère les propriétés de membre.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un élément valide `HRESULT`, généralement `S_OK`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProperty (Interface)](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [IDebugPropertyEnumType_All (Interface)](../../winscript/reference/idebugpropertyenumtype-all-interface.md)   
 [Interface IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)