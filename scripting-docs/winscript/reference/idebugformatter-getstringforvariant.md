---
title: 'IDebugFormatter :: GetStringForVariant | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugFormatter.GetStringForVariant
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugFormatter::GetStringForVariant
ms.assetid: 95189d03-1126-433e-8513-659107b3df16
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f703396190f1fb7791306ee9e389b676e749f8f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576367"
---
# <a name="idebugformattergetstringforvariant"></a>IDebugFormatter::GetStringForVariant
Retourne une chaîne qui représente la valeur de variante donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetStringForVariant(  
   VARIANT*  pvar,  
   ULONG     nRadix,  
   BSTR*     pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pvar`  
 dans VARIANT à représenter sous la forme d’une chaîne.  
  
 `nRadix`  
 dans Base à utiliser pour les valeurs numériques.  
  
 `pbstrValue`  
 à Chaîne représentant `pvar`.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne une chaîne qui représente la valeur de variante donnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugFormatter](../../winscript/reference/idebugformatter-interface.md)