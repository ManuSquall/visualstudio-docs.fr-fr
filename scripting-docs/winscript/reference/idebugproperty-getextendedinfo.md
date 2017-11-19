---
title: IDebugProperty::GetExtendedInfo | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugProperty.GetExtendedInfo
apilocation: scrobj.dll
helpviewer_keywords: IDebugProperty::GetExtendedInfo
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc549ecc4cfa3b3cbbb754585c751b16df2fd8a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
Obtient les informations étendues pour la propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cInfos`  
 [in] Nombre d’objets étendus.  
  
 `rgguidExtendedInfo`  
 [in] Un tableau de `GUID`s est passé afin que plusieurs éléments d’informations étendues peuvent être récupérées en même temps.  
  
 `pExtendedInfo`  
 [out] Retourne un tableau de `VARIANT`qui peut être utilisé pour récupérer les informations de propriété étendue.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un élément valide `HRESULT`, généralement `S_OK`.  
  
## <a name="remarks"></a>Remarques  
 Cette interface obtient les étendues des informations pour cet objet. L’API existe uniquement à des fins de récupération des informations qui ne se prêtent pas à être récupérés par l’utilisation de `IDebugProperty::GetPropertyInfo`).  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)