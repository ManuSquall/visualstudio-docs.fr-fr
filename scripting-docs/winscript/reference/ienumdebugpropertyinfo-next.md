---
title: IEnumDebugPropertyInfo::Next | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumDebugPropertyInfo.Next
apilocation: scrobj.dll
helpviewer_keywords: IEnumDebugPropertyInfo::Next
ms.assetid: 052837ac-1599-49cc-9a5a-ba90f992eeff
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc1e25a865ab1e21ab011e3a5bd0cc3b74f4abf2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugpropertyinfonext"></a>IEnumDebugPropertyInfo::Next
Récupère un nombre spécifié de `DebugPropertyInfo` structures dans une séquence d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Next (  
   ULONGcelt,  
   DebugPropertyInfo*rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celt`  
 [in] Le nombre de `DebugPropertyInfo`structures doit être récupéré.  
  
 `rgelt`  
 [out] Un tableau de `DebugPropertyInfo` extraites des structures.  
  
 `pceltFetched`  
 [out] Retourne le nombre de `DebugPropertyInfo` structures réellement récupérées.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un élément valide `HRESULT`, généralement `S_OK`.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumDebugPropertyInfo (Interface)](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [Structure DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)