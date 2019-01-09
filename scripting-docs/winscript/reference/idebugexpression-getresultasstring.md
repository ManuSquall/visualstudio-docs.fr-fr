---
title: IDebugExpression::GetResultAsString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsString
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6cee33b5547e30f913407b02a3befd449dda6aeb
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097355"
---
# <a name="idebugexpressiongetresultasstring"></a>IDebugExpression::GetResultAsString
Retourne le résultat de l’évaluation de l’expression comme une chaîne et la valeur de retour de l’opération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `phrResult`  
 [out] Valeur de retour de l’opération.  
  
 `pbstrResult`  
 [out] Le résultat de l’évaluation d’expression.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_PENDING`|L’opération est toujours en attente.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne le résultat de l’évaluation des expressions en tant que chaîne et l’opération `HRESULT`.  
  
 Cette méthode retourne `S_OK` et `phrResult` retourne `E_ABORT` si `Abort` abandonne l’opération.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugExpression](../../winscript/reference/idebugexpression-interface.md)