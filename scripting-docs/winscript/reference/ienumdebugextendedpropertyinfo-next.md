---
title: 'IEnumDebugExtendedPropertyInfo :: suivant | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 23ebc3e3fd1f7802f4630be42a594d73f8657e43
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574260"
---
# <a name="ienumdebugextendedpropertyinfonext"></a>IEnumDebugExtendedPropertyInfo::Next
Récupère un nombre spécifié de structures de `ExtendedDebugPropertyInfo` dans une séquence d’énumération.  
  
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
 dans Nombre de `ExtendedDebugPropertyInfo`structures à récupérer.  
  
 `rgelt`  
 à Tableau de `ExtendedDebugPropertyInfo` structures récupérées.  
  
 `pceltFetched`  
 à Nombre de structures de `ExtendedDebugPropertyInfo` réellement récupérées.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un `HRESULT` valide, généralement `S_OK`.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IEnumDebugExtendedPropertyInfo](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)  
 [Structure ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)