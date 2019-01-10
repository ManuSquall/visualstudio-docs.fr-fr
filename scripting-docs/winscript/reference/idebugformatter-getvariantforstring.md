---
title: IDebugFormatter::GetVariantForString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 1ee40057043751b465c6575575f00dee848a0160
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086617"
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