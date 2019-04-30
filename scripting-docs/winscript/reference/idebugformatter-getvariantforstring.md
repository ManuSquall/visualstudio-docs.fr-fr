---
title: IDebugFormatter::GetVariantForString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugFormatter.GetVariantForString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugFormatter::GetVariantForString
ms.assetid: 2993431d-0ee2-4d8d-b62c-0a810a8bc391
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea6cd1f77481282700de492e2857046044a04e2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979287"
---
# <a name="idebugformattergetvariantforstring"></a>IDebugFormatter::GetVariantForString
Retourne une valeur VARIANT contenant la chaîne donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetVariantForString(  
   LPCOLESTR  pwstrValue,  
   VARIANT*   pvar  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pwstrValue`  
 [in] Chaîne à stocker dans un VARIANT.  
  
 `pvar`  
 [out] VARIANT contenant `pwstrValue`.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne une valeur VARIANT contenant la chaîne donnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugFormatter](../../winscript/reference/idebugformatter-interface.md)