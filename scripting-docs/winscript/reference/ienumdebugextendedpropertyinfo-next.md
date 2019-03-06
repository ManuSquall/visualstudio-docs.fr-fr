---
title: IEnumDebugExtendedPropertyInfo::Next | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.Next
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::Next
ms.assetid: ac41c9a3-19d1-4596-8a87-01c10b131be3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2694ba3a1ddb70127de5ba3b197cd044f3b6b9af
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086319"
---
# <a name="ienumdebugextendedpropertyinfonext"></a>IEnumDebugExtendedPropertyInfo::Next
Récupère un nombre spécifié de`ExtendedDebugPropertyInfo` structures dans une séquence d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Next (  
   ULONGcelt,  
   ExtendedDebugPropertyInfo *rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celt`  
 [in] Le nombre de `ExtendedDebugPropertyInfo`structures à récupérer.  
  
 `rgelt`  
 [out] Un tableau de `ExtendedDebugPropertyInfo` structures récupérées.  
  
 `pceltFetched`  
 [out] Le nombre de `ExtendedDebugPropertyInfo` structures réellement récupérées.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une liste valide `HRESULT`, généralement `S_OK`.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumDebugExtendedPropertyInfo (Interface)](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [Structure ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)