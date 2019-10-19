---
title: 'IVariantChangeType :: ChangeType | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IVariantChangeType.ChangeType
apilocation:
- scrobj.dll
helpviewer_keywords:
- IVariantChangeType::ChangeType
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 406d5d8486b3016f0105b7bd8bf231db0e1e9613
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571783"
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
Prend une valeur de type Variant et crée un nouveau variant avec un type spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pvarDst`  
 [in, out] Variant pour contenir la valeur représentée par `pvarSrc`, mais avec le type spécifié par `vtNew`.  
  
 `pvarSrc`  
 dans Valeur de type Variant à modifier dans un nouveau type.  
  
 `lcid`  
 dans Contexte des paramètres régionaux à utiliser lors de la conversion des arguments vers ou à partir de chaînes.  
  
 `vtNew`  
 dans Spécifie le type de `pvarDst` à transformer.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Les arguments `pvarDst` et `pvarSrc` peuvent être égaux, auquel cas la valeur d’origine est remplacée. Cette méthode passe `pvarDst` à la fonction `VariantClear` et, par conséquent, `pvarDst` doit être initialisée à une valeur valide.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IVariantChangeType](../../winscript/reference/ivariantchangetype-interface.md)