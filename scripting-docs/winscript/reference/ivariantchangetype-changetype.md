---
title: IVariantChangeType::ChangeType | Microsoft Docs
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
ms.openlocfilehash: 81ed0a8502e9b0cfc53725621d477d34ee5010ea
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58158579"
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
Prend une valeur variante et crée une nouvelle variante avec un type spécifié.  
  
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
 [in, out] Un variant pour contenir la valeur représentée par `pvarSrc`, mais avec le type spécifié par `vtNew`.  
  
 `pvarSrc`  
 [in] Une valeur de type variant à modifier dans un nouveau type.  
  
 `lcid`  
 [in] Contexte des paramètres régionaux à utiliser lors de la conversion des arguments vers ou à partir de chaînes.  
  
 `vtNew`  
 [in] Spécifie le type pour `pvarDst` pour devenir.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Le `pvarDst` et `pvarSrc` des arguments peuvent être égales, auquel cas la valeur d’origine est remplacée. Cette méthode passe `pvarDst` à la `VariantClear` (fonction) et par conséquent `pvarDst` doit être initialisé avec une valeur valide.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IVariantChangeType](../../winscript/reference/ivariantchangetype-interface.md)