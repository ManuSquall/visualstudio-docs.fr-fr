---
title: IDebugHelper::CreateSimpleConnectionPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreateSimpleConnectionPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreateSimpleConnectionPoint
ms.assetid: 5e4798ce-6f9f-4184-9853-67bf8c8524ab
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f909a63f0f7ba70fca3c5e30e32a2d64c0147e9c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979173"
---
# <a name="idebughelpercreatesimpleconnectionpoint"></a>IDebugHelper::CreateSimpleConnectionPoint
Retourne une interface d’événement qui encapsule une donnée `IDispatch` objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CreateSimpleConnectionPoint(  
   IDispatch*                pdisp  
   ISimpleConnectionPoint**  ppscp  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdisp`  
 [in] Le `IDispatch` objet à encapsuler.  
  
 `ppscp`  
 [out] L’interface d’événement qui encapsule `pdisp`.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Retourne une interface d’événement qui encapsule la donnée `IDispatch` (consultez [ISimpleConnectionPoint (Interface)](../../winscript/reference/isimpleconnectionpoint-interface.md)).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugHelper (Interface)](../../winscript/reference/idebughelper-interface.md)   
 [Interface ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)