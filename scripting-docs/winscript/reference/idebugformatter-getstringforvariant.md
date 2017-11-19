---
title: IDebugFormatter::GetStringForVariant | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugFormatter.GetStringForVariant
apilocation: jscript.dll
helpviewer_keywords: IDebugFormatter::GetStringForVariant
ms.assetid: 95189d03-1126-433e-8513-659107b3df16
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bfc31b0fdbf6d1f4a29b1322dc3a3c4015f9c8ff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugformattergetstringforvariant"></a>IDebugFormatter::GetStringForVariant
Retourne une chaîne qui représente la valeur de type VARIANT donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetStringForVariant(  
   VARIANT*  pvar,  
   ULONG     nRadix,  
   BSTR*     pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pvar`  
 [in] VARIANTE pour représenter sous forme de chaîne.  
  
 `nRadix`  
 [in] Base à utiliser pour les valeurs numériques.  
  
 `pbstrValue`  
 [out] Chaîne représentant `pvar`.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode retourne une chaîne qui représente la valeur de type variant donnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugFormatter](../../winscript/reference/idebugformatter-interface.md)