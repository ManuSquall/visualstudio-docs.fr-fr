---
title: IDebugExpression::GetResultAsDebugProperty | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsDebugProperty
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsDebugProperty
ms.assetid: 9075bf2f-d5bb-464e-b6c2-3fa3215e9ae0
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06d9b513d40450e20bb87f07c460bef7ce2678c1
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148019"
---
# <a name="idebugexpressiongetresultasdebugproperty"></a>IDebugExpression::GetResultAsDebugProperty
Retourne le résultat de l’évaluation des expressions en tant que propriété de débogage et de la valeur de retour de l’opération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetResultAsDebugProperty(  
   HRESULT*          phrResult,  
   IDebugProperty**  ppdp  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `phrResult`  
 [out] Valeur de retour de l’opération.  
  
 `ppdp`  
 [out] La propriété de débogage pour l’expression.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_PENDING`|L’opération est toujours en attente.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne le résultat de l’évaluation d’expression comme un `IDebugProperty` et l’opération `HRESULT`.  
  
 Cette méthode retourne `S_OK` et `phrResult` retourne `E_ABORT` si `Abort` abandonne l’opération.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExpression (Interface)](../../winscript/reference/idebugexpression-interface.md)   
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)