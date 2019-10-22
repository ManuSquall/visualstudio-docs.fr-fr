---
title: 'IPerPropertyBrowsing2 :: SetPredefinedValue | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.SetPredefinedValue
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::SetPredefinedValue
ms.assetid: 3aff5300-c5a4-4d9b-9d47-a75b64014ac4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a823a04082b7e19b2c1bc475c1070cc501789e8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576232"
---
# <a name="iperpropertybrowsing2setpredefinedvalue"></a>IPerPropertyBrowsing2::SetPredefinedValue
Définit la valeur de la propriété spécifiée par `dispID`. La valeur prédéfinie est identifiée par le jeton `dwCookie.`  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetPredefinedValue(  
   DISPID  dispid,  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dispid`  
 dans Identificateur de dispatch de la propriété pour laquelle une valeur prédéfinie est définie.  
  
 `dwCookie`  
 dans Jeton identifiant la valeur à définir.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un `HRESULT` valide, généralement `S_OK`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface 1 IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)