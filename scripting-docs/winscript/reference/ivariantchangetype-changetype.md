---
title: IVariantChangeType::ChangeType | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IVariantChangeType.ChangeType
apilocation: scrobj.dll
helpviewer_keywords: IVariantChangeType::ChangeType
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d742d1bd57c85aa75c9ccd60479d08c1a559fb37
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
Prend une valeur variante et crée une nouvelle variante avec un type spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pvarDst`  
 [dans, out] Un variant pour contenir la valeur représentée par `pvarSrc`, mais avec le type spécifié par `vtNew`.  
  
 `pvarSrc`  
 [in] Une valeur de type variant à modifier dans un nouveau type.  
  
 `lcid`  
 [in] Contexte des paramètres régionaux à utiliser lors de la conversion des arguments vers ou à partir de chaînes.  
  
 `vtNew`  
 [in] Spécifie le type de `pvarDst` devienne.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Le `pvarDst` et `pvarSrc` des arguments peuvent être égales, auquel cas la valeur d’origine est remplacée. Cette méthode passe `pvarDst` à la `VariantClear` (fonction) et par conséquent `pvarDst` doit être initialisé à une valeur valide.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IVariantChangeType](../../winscript/reference/ivariantchangetype-interface.md)