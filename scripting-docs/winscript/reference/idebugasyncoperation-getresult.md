---
title: IDebugAsyncOperation::GetResult | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugAsyncOperation.GetResult
apilocation: pdm.dll
helpviewer_keywords: IDebugAsyncOperation::GetResult
ms.assetid: 56d43365-6b12-4213-a97c-953c40d7b7f6
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60181904408010f35fa4d99d182216e665583aab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperationgetresult"></a>IDebugAsyncOperation::GetResult
Fournit la valeur de retour et le paramètre d’objet de retour à partir de l’opération de débogage synchrone.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `phrResult`  
 [out] Si l’opération est terminée, `phrResult` est la valeur de retour de `IDebugSyncOperation::Execute`.  
  
 `ppunkResult`  
 [out] Si l’opération est terminée, `ppunkResult` est le paramètre de l’objet retourné par l’opération.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_PENDING`|L’opération n’est pas terminée.|  
  
## <a name="remarks"></a>Remarques  
 Si l’opération est terminée, cette méthode retourne le `HRESULT` et le paramètre à partir de l’objet `IDebugSyncOperation::Execute`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugAsyncOperation (Interface)](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)