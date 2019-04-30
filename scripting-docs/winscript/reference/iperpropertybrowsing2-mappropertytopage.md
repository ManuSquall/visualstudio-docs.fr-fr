---
title: IPerPropertyBrowsing2::MapPropertyToPage | Microsoft Docs
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
ms.openlocfilehash: 77270bbe963f281a43a085cb7d15724b7b2ec14e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944830"
---
# <a name="iperpropertybrowsing2mappropertytopage"></a>IPerPropertyBrowsing2::MapPropertyToPage
Retourne le CLSID de la page de propriété qui peut être utilisé pour modifier cette propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT MapPropertyToPage(  
   DISPID  dispid,  
   CLSID*  pClsidPropPage  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dispid`  
 [in] Identificateur de dispatch de la propriété qui vous intéresse.  
  
 `pClsidPropPage`  
 [out] Pointeur vers le CLSID identifiant la page de propriété associée à la propriété. Si cette méthode échoue, *`pClsidPropPage` a la valeur CLSID_NULL.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une liste valide `HRESULT`, généralement `S_OK`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface 1 IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)