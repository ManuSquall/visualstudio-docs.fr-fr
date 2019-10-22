---
title: 'IDebugAsyncOperation :: GetResult | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.GetResult
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::GetResult
ms.assetid: 56d43365-6b12-4213-a97c-953c40d7b7f6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55c51649a5bc3094dd306166e013a892ce67e236
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573287"
---
# <a name="idebugasyncoperationgetresult"></a>IDebugAsyncOperation::GetResult
Fournit la valeur de retour et le paramètre d’objet de retour de l’opération de débogage synchrone.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `phrResult`  
 à Si l’opération est terminée, `phrResult` est la valeur de retour de `IDebugSyncOperation::Execute`.  
  
 `ppunkResult`  
 à Si l’opération est terminée, `ppunkResult` est le paramètre d’objet retourné par l’opération.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_PENDING`|L’opération n’est pas terminée.|  
  
## <a name="remarks"></a>Notes  
 Si l’opération est terminée, cette méthode retourne le `HRESULT` et le paramètre d’objet à partir de `IDebugSyncOperation::Execute`.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)  
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)