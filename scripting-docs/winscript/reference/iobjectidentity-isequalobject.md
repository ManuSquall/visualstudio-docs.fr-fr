---
title: IObjectIdentity::IsEqualObject | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 52e386055e458568f8d4076a37489b7b2397f399
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728599"
---
# <a name="iobjectidentityisequalobject"></a>IObjectIdentity::IsEqualObject
Détermine si un objet est égal à l’objet actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsEqualObject(  
  IUnknown*punk  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `punk`  
 [in] Adresse de l’objet à comparer à l’objet actuel.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|Les objets sont égaux.|  
|`S_FALSE`|Les objets ne sont pas égaux.|  
  
## <a name="remarks"></a>Remarques  
 Une implémentation de la `IsEqualObject` méthode doit retourner `S_OK` uniquement si les objets sont identiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IObjectIdentity](../../winscript/reference/iobjectidentity-interface.md)