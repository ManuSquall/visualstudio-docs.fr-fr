---
title: 'IDebugExpression :: GetResultAsDebugProperty | Microsoft Docs'
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
ms.openlocfilehash: 104c42f02d02be386711e687f02d333425834948
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575924"
---
# <a name="idebugexpressiongetresultasdebugproperty"></a>IDebugExpression::GetResultAsDebugProperty
Retourne le résultat de l’évaluation de l’expression sous la forme d’une propriété de débogage et de la valeur de retour de l’opération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetResultAsDebugProperty(  
   HRESULT*          phrResult,  
   IDebugProperty**  ppdp  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `phrResult`  
 à Valeur de retour de l’opération.  
  
 `ppdp`  
 à Propriété de débogage pour l’expression.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_PENDING`|L’opération est toujours en attente.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne le résultat de l’évaluation de l’expression sous la forme d’un `IDebugProperty` et de l' `HRESULT` de l’opération.  
  
 Cette méthode retourne `S_OK` et `phrResult` retourne `E_ABORT` si `Abort` abandonne l’opération.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugExpression](../../winscript/reference/idebugexpression-interface.md)  
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)