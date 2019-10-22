---
title: 'IDebugHelper :: CreateSimpleConnectionPoint | Microsoft Docs'
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
ms.openlocfilehash: 06324b0d10eb6d0d69b6426276d5df7f382d2abe
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562459"
---
# <a name="idebughelpercreatesimpleconnectionpoint"></a>IDebugHelper::CreateSimpleConnectionPoint
Retourne une interface d’événement qui encapsule un objet `IDispatch` donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CreateSimpleConnectionPoint(  
   IDispatch*                pdisp  
   ISimpleConnectionPoint**  ppscp  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdisp`  
 dans Objet `IDispatch` à inclure dans un wrapper.  
  
 `ppscp`  
 à Interface d’événement qui encapsule `pdisp`.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Retourne une interface d’événement qui encapsule le `IDispatch` donné (voir [interface ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)).  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugHelper](../../winscript/reference/idebughelper-interface.md)  
 [Interface ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)