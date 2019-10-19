---
title: ISimpleConnectionPoint ::D escribeEvents | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.DescribeEvents
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::DescribeEvents
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5000689d588fe3f63ec5408893187bba8d13d63
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571822"
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
Retourne le DISPID et le nom de chaque événement dans une plage d’événements spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT DescribeEvents(  
   ULONG    iEvent,  
   ULONG    cEvents,  
   DISPID*  prgid,  
   BSTR*    prgbstr,  
   ULONG*   pcEventsFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `iEvent`  
 dans Index du premier événement à récupérer.  
  
 `cEvents`  
 dans Nombre d’événements à récupérer.  
  
 `prgid`  
 à Tableau de valeurs de l’événement DISPID.  
  
 `prgbstr`  
 à Tableau de noms d’événements.  
  
 `pcEventsFetched`  
 à Nombre réel d’événements récupérés.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`S_FALSE`|Plus d’événements ont été demandés que ceux disponibles. Les événements non disponibles sont représentés par DISPID_NULL et un BSTR null.|  
|`E_INVALIDARG`|Aucun élément n’a pu être extrait.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne le DISPID et le nom de chaque événement dans une plage d’événements spécifiée.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)