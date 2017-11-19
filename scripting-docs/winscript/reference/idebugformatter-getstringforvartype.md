---
title: IDebugFormatter::GetStringForVarType | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugFormatter.GetStringForVarType
apilocation: jscript.dll
helpviewer_keywords: IDebugFormatter::GetStringForVarType
ms.assetid: 1c1a0499-ca57-47e0-8367-fdb4c902bca3
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e056fa2ef9613c1af776840d1dae61078e26f83
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugformattergetstringforvartype"></a>IDebugFormatter::GetStringForVarType
Retourne une chaîne qui représente la valeur VARTYPE spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetStringForVarType(  
   VARTYPE    vt,  
   TYPEDESC*  ptdescArrayType,  
   BSTR*      pbstr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `vt`  
 [in] VARTYPE pour représenter sous forme de chaîne.  
  
 `ptdescArrayType`  
 [in] Tableau de structures qui décrit les types.  
  
 `pbstr`  
 [out] Chaîne représentant `vt`.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 La méthode retourne une chaîne qui représente la valeur VARTYPE spécifiée.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugFormatter](../../winscript/reference/idebugformatter-interface.md)