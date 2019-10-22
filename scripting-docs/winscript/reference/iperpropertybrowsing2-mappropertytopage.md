---
title: 'IPerPropertyBrowsing2 :: MapPropertyToPage | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.MapPropertyToPage
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::MapPropertyToPage
ms.assetid: e6418a8e-500b-42e1-9b5a-52e6f7567f99
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e9e3f821d9e02be567f970d8db1c238ee5cebd29
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577128"
---
# <a name="iperpropertybrowsing2mappropertytopage"></a>IPerPropertyBrowsing2::MapPropertyToPage
Retourne le CLSID de la page de propriétés qui peut être utilisée pour modifier cette propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT MapPropertyToPage(  
   DISPID  dispid,  
   CLSID*  pClsidPropPage  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dispid`  
 dans Identificateur de dispatch de la propriété qui vous intéresse.  
  
 `pClsidPropPage`  
 à Pointeur vers le CLSID identifiant la page de propriétés associée à la propriété. Si cette méthode échoue, * `pClsidPropPage` est défini sur CLSID_NULL.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un `HRESULT` valide, généralement `S_OK`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface 1 IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)