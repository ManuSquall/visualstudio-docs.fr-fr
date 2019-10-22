---
title: 'IDebugHelper :: CreatePropertyBrowserEx | Microsoft Docs'
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
ms.openlocfilehash: 4d64d9dad54e029dc4c76e8b7e6c7a3f0299b0cb
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576502"
---
# <a name="idebughelpercreatepropertybrowserex"></a>IDebugHelper::CreatePropertyBrowserEx
Retourne un Explorateur de propriétés qui encapsule une variante et permet la conversion personnalisée de valeurs de type VARIANT ou de types VARTYPE en chaînes.  
  
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
 dans Variante racine à parcourir.  
  
 `bstrName`  
 dans Nom à attribuer à la racine.  
  
 `pdat`  
 dans Thread sur lequel demander des propriétés. Si ce paramètre a la valeur NULL, aucun marshaling n’est effectué.  
  
 `pdf`  
 dans Objet qui fournit une mise en forme personnalisée pour les variantes.  
  
 `ppdob`  
 à Explorateur de propriétés.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne un Explorateur de propriétés qui encapsule une variante et permet la conversion personnalisée de valeurs de type VARIANT ou de types VARTYPE en chaînes.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugHelper :: CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)    
 @No__t_1 de l' [interface IDebugHelper](../../winscript/reference/idebughelper-interface.md)  
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)