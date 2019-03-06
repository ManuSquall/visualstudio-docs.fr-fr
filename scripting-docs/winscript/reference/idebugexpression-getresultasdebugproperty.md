---
title: IDebugExpression::GetResultAsDebugProperty | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 6aebe983c33416d1c3d12d18c272fd1e4de27467
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093104"
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