---
title: IDebugHelper::CreatePropertyBrowserEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreatePropertyBrowserEx
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreatePropertyBrowserEx
ms.assetid: 87ad322f-09da-4ce8-bb68-0b0bbeec645b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 01e63d1588fd1e25f3415f22450ed5145752d711
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144574"
---
# <a name="idebughelpercreatepropertybrowserex"></a>IDebugHelper::CreatePropertyBrowserEx
Retourne un Explorateur de propriétés qui encapsule une variante et permet la conversion personnalisée de valeurs de type VARIANT ou types VARTYPE en chaînes.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CreatePropertyBrowserEx(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugFormatter*          pdf,  
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
  
 `pdf`  
 [in] Objet qui fournit la mise en forme personnalisée pour les variantes.  
  
 `ppdob`  
 [out] L’Explorateur de propriétés.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne un Explorateur de propriétés qui encapsule une variante et permet la conversion personnalisée de valeurs de type VARIANT ou types VARTYPE en chaînes.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)   
 [IDebugHelper (Interface)](../../winscript/reference/idebughelper-interface.md)   
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)