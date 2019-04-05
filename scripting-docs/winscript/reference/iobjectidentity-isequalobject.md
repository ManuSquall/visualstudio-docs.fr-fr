---
title: IObjectIdentity::IsEqualObject | Microsoft Docs
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
ms.openlocfilehash: c215a15a1239f07272079783366a1617c3a626e2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58156032"
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
 [in] Adresse de l’objet à comparer avec l’objet actuel.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|Les objets sont égaux.|  
|`S_FALSE`|Les objets ne sont pas égaux.|  
  
## <a name="remarks"></a>Notes  
 Une implémentation de la `IsEqualObject` méthode doit retourner `S_OK` uniquement si les objets sont identiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IObjectIdentity](../../winscript/reference/iobjectidentity-interface.md)