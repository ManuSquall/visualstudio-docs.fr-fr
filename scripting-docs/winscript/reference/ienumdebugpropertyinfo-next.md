---
title: IEnumDebugPropertyInfo::Next | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Next
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Next
ms.assetid: 052837ac-1599-49cc-9a5a-ba90f992eeff
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24835d4d17cacae44a3eb4593b6292ada4672ccb
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096367"
---
# <a name="ienumdebugpropertyinfonext"></a>IEnumDebugPropertyInfo::Next
Récupère un nombre spécifié de `DebugPropertyInfo` structures dans une séquence d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Next (  
   ULONGcelt,  
   DebugPropertyInfo*rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celt`  
 [in] Le nombre de `DebugPropertyInfo`structures à récupérer.  
  
 `rgelt`  
 [out] Un tableau de `DebugPropertyInfo` structures récupérées.  
  
 `pceltFetched`  
 [out] Retourne le nombre de `DebugPropertyInfo` structures réellement récupérées.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une liste valide `HRESULT`, généralement `S_OK`.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumDebugPropertyInfo (Interface)](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [Structure DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)