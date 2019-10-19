---
title: 'ISimpleConnectionPoint :: GetEventCount | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.GetEventCount
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::GetEventCount
ms.assetid: f1527d5b-6076-4536-8e59-e55da741ef39
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3cfa392a052d415cef4c19f07c6c8e73704dfa45
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571808"
---
# <a name="isimpleconnectionpointgeteventcount"></a>ISimpleConnectionPoint::GetEventCount
Retourne le nombre d’événements exposés sur cette interface.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetEventCount(  
   ULONG*  pulCount  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pulCount`  
 à Nombre d’événements exposés sur ce nombre d’interfaces.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne le nombre d’événements exposés sur cette interface.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)