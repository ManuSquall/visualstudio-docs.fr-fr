---
title: IPerPropertyBrowsing2::MapPropertyToPage | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IPerPropertyBrowsing2.MapPropertyToPage
apilocation: scrobj.dll
helpviewer_keywords: IPerPropertyBrowsing2::MapPropertyToPage
ms.assetid: e6418a8e-500b-42e1-9b5a-52e6f7567f99
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 79b8d7cb9e1c8a9f79cdddc4f8d3404ff7a2036c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iperpropertybrowsing2mappropertytopage"></a>IPerPropertyBrowsing2::MapPropertyToPage
Retourne le CLSID de la page de propriétés qui peut être utilisé pour modifier cette propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 Retourne un élément valide `HRESULT`, généralement `S_OK`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface 1 IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)