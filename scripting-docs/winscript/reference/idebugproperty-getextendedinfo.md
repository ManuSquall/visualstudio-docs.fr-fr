---
title: IDebugProperty::GetExtendedInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetExtendedInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetExtendedInfo
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 707474f786a8f88c0e08d887f2c2b09c8aaedc8e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144860"
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
Obtient les informations étendues pour la propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cInfos`  
 [in] Nombre d’objets d’informations étendues.  
  
 `rgguidExtendedInfo`  
 [in] Un tableau de `GUID`s est passé afin que plusieurs éléments d’informations étendues peuvent être récupérées en même temps.  
  
 `pExtendedInfo`  
 [out] Retourne un tableau de `VARIANT`s qui peut être utilisé pour récupérer les informations de propriété étendue.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une liste valide `HRESULT`, généralement `S_OK`.  
  
## <a name="remarks"></a>Notes  
 Cette interface obtient les étendues info pour cet objet. L’API existe uniquement à des fins de récupération des informations qui ne se prêtent pas à leur récupération par l’utilisation de `IDebugProperty::GetPropertyInfo`).  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)