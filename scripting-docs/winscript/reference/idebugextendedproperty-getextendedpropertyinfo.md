---
title: IDebugExtendedProperty::GetExtendedPropertyInfo | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugExtendedProperty.GetExtendedPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: IDebugExtendedProperty::GetExtendedPropertyInfo
ms.assetid: 56edf538-5082-4653-82b6-e6640d6f61ba
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7109346dd8189395cfdd366ff622dfac00744382
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugextendedpropertygetextendedpropertyinfo"></a>IDebugExtendedProperty::GetExtendedPropertyInfo
Récupère les informations étendues pour une propriété étendue, qui est le plus d’informations que le plus simple `IDebugProperty`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetExtendedPropertyInfo(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   ExtendedDebugPropertyInfo*  pExtendedPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwFieldSpec`  
 [in] Spécifie les constantes EX_DBGPROP_INFO_FLAGS qui déterminent les champs à être rempli le `ExtendedDebugPropertyInfo` structure.  
  
 `nRadix`  
 [in] Base à utiliser pour l’interprétation des informations numériques.  
  
 `pExtendedPropertyInfo`  
 [out] Retourne le `ExtendedDebugPropertyInfo` structure qui décrit la propriété.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un élément valide `HRESULT`, généralement `S_OK`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExtendedProperty (Interface)](../../winscript/reference/idebugextendedproperty-interface.md)   
 [EX_DBGPROP_INFO_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)   
 [Structure ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)