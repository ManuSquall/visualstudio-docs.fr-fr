---
title: IDebugHelper::CreatePropertyBrowser | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreatePropertyBrowser
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreatePropertyBrowser
ms.assetid: 2fa819cf-c7f7-4bd7-b018-ea33b804ba8f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c3eedf9d6ed07b510d7912a5b28d23e0a1f05dda
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087748"
---
# <a name="idebughelpercreatepropertybrowser"></a>IDebugHelper::CreatePropertyBrowser
Retourne un Explorateur de propriétés qui encapsule une variante.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CreatePropertyBrowser(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugProperty**          ppdob  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pvar`  
 [in] Variante de racine à parcourir.  
  
 `bstrName`  
 [in] Nom à attribuer à la racine.  
  
 `pdat`  
 [in] Thread sur lequel les propriétés de la demande. Si ce paramètre est NULL, aucun marshaling n’est effectuée.  
  
 `ppdob`  
 [out] L’Explorateur de propriétés.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne un Explorateur de propriétés qui encapsule une variante.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)   
 [IDebugHelper (Interface)](../../winscript/reference/idebughelper-interface.md)   
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)