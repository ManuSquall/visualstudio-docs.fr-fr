---
title: 'IObjectIdentity :: IsEqualObject | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IObjectIdentity.IsEqualObject
apilocation:
- scrobj.dll
helpviewer_keywords:
- IsEqualObject method
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 636dfa07b1fc94dfec2273220aa4101f5cd085b1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571462"
---
# <a name="iobjectidentityisequalobject"></a>IObjectIdentity::IsEqualObject
Détermine si un objet est égal à l’objet actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT IsEqualObject(  
  IUnknown*punk  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `punk`  
 dans Adresse de l’objet à comparer à l’objet actuel.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|Les objets sont égaux.|  
|`S_FALSE`|Les objets ne sont pas égaux.|  
  
## <a name="remarks"></a>Notes  
 Une implémentation de la méthode `IsEqualObject` doit retourner `S_OK` uniquement si les objets sont identiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IObjectIdentity](../../winscript/reference/iobjectidentity-interface.md)