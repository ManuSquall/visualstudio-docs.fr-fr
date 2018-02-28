---
title: IDebugHelper::CreatePropertyBrowser | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugHelper.CreatePropertyBrowser
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreatePropertyBrowser
ms.assetid: 2fa819cf-c7f7-4bd7-b018-ea33b804ba8f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f728068b6d1db6fe70a084ae680f32a78a0a2760
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebughelpercreatepropertybrowser"></a>IDebugHelper::CreatePropertyBrowser
Retourne un Explorateur de propriétés qui encapsule une variante.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreatePropertyBrowser(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugProperty**          ppdob  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pvar`  
 [in] Parcourir la variante de racine.  
  
 `bstrName`  
 [in] Nom à attribuer à la racine.  
  
 `pdat`  
 [in] Thread sur lequel demander des propriétés. Si ce paramètre est NULL, aucun marshaling n’est effectué.  
  
 `ppdob`  
 [out] L’Explorateur de propriétés.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode retourne un Explorateur de propriétés qui encapsule une variante.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)   
 [IDebugHelper (Interface)](../../winscript/reference/idebughelper-interface.md)   
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)