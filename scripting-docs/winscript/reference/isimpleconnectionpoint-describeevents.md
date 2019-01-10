---
title: ISimpleConnectionPoint::DescribeEvents | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 43a20a2d9580c80bc6aea5d22c6a0713f4843634
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088502"
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
Retourne le DISPID pour chaque événement dans une plage spécifiée d’événements.  
  
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
 [in] Index du premier événement à récupérer.  
  
 `cEvents`  
 [in] Nombre d’événements à récupérer.  
  
 `prgid`  
 [out] Tableau de DISPID des valeurs d’événement.  
  
 `prgbstr`  
 [out] Tableau des noms d’événement.  
  
 `pcEventsFetched`  
 [out] Le nombre réel d’événements extraites.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`S_FALSE`|Plusieurs événements ont été demandées qu’étaient disponibles. Événements indisponibles sont représentés par DISPID_NULL et un BSTR null.|  
|`E_INVALIDARG`|Aucun élément ne peut être extraite.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne le DISPID et le nom de chaque événement dans une plage spécifiée d’événements.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)