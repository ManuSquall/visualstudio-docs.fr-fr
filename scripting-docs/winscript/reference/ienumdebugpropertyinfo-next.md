---
title: 'IEnumDebugPropertyInfo :: suivant | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: b99631c217ca56dce91512403dfb6623cd1e7641
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574195"
---
# <a name="ienumdebugpropertyinfonext"></a>IEnumDebugPropertyInfo::Next
Récupère un nombre spécifié de structures de `DebugPropertyInfo` dans une séquence d’énumération.  
  
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
 dans Nombre de `DebugPropertyInfo`structures à récupérer.  
  
 `rgelt`  
 à Tableau de `DebugPropertyInfo` structures récupérées.  
  
 `pceltFetched`  
 à Retourne le nombre de structures de `DebugPropertyInfo` réellement récupérées.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un `HRESULT` valide, généralement `S_OK`.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)  
 [Structure DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)