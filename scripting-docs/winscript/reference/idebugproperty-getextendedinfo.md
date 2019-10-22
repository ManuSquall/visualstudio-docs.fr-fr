---
title: 'IDebugProperty :: GetExtendedInfo | Microsoft Docs'
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
ms.openlocfilehash: 130d11c8ed6bb21210d129bb9aace779db3bd54b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562389"
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
Obtient des informations étendues pour la propriété.  
  
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
 dans Nombre d’objets d’informations étendues.  
  
 `rgguidExtendedInfo`  
 dans Un tableau de `GUID`s est passé afin que plusieurs éléments d’informations étendues puissent être récupérés en même temps.  
  
 `pExtendedInfo`  
 à Retourne un tableau d' `VARIANT`s qui peut être utilisé pour récupérer les informations sur les propriétés étendues.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un `HRESULT` valide, généralement `S_OK`.  
  
## <a name="remarks"></a>Notes  
 Cette interface obtient des informations étendues pour cet objet. L’API existe uniquement dans le but de récupérer des informations qui ne se prêtent pas à être récupérées par l’utilisation de `IDebugProperty::GetPropertyInfo`).  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)