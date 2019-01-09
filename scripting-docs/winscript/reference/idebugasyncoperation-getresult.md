---
title: IDebugAsyncOperation::GetResult | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: d86e9eb2b934bc6bd4027405d06960cd107f81c1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087475"
---
# <a name="idebugasyncoperationgetresult"></a>IDebugAsyncOperation::GetResult
Fournit la valeur de retour et le paramètre d’objet de retour à partir de l’opération de débogage synchrone.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `phrResult`  
 [out] Si l’opération est terminée, `phrResult` est la valeur de retour de `IDebugSyncOperation::Execute`.  
  
 `ppunkResult`  
 [out] Si l’opération est terminée, `ppunkResult` est le paramètre d’objet retourné par l’opération.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_PENDING`|L’opération n’est pas terminée.|  
  
## <a name="remarks"></a>Notes  
 Si l’opération est terminée, cette méthode retourne le `HRESULT` et le paramètre à partir de l’objet `IDebugSyncOperation::Execute`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugAsyncOperation (Interface)](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)