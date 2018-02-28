---
title: ISimpleConnectionPoint::DescribeEvents | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ISimpleConnectionPoint.DescribeEvents
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::DescribeEvents
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 42dab9558d46eae0fbb640c60264a79877708321
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
Retourne le DISPID et le nom de chaque événement dans une plage spécifiée d’événements.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] Index du premier événement à récupérer.  
  
 `cEvents`  
 [in] Nombre d’événements à récupérer.  
  
 `prgid`  
 [out] Tableau de valeurs DISPID d’événement.  
  
 `prgbstr`  
 [out] Tableau des noms d’événements.  
  
 `pcEventsFetched`  
 [out] Le nombre réel d’événements extraites.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`S_FALSE`|Plusieurs événements ont été demandées que. Événements indisponibles sont représentés par DISPID_NULL et un BSTR null.|  
|`E_INVALIDARG`|Aucun élément ne peut être récupérés.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode retourne le DISPID et le nom de chaque événement dans une plage spécifiée d’événements.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)