---
title: 'IDebugAsyncOperation :: GetSyncDebugOperation | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.GetSyncDebugOperation
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::GetSyncDebugOperation
ms.assetid: ff89a3bc-57d7-4cb9-9818-8d73ed71af73
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d732b732681216c0e9eecec7f448bf263376d8c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573273"
---
# <a name="idebugasyncoperationgetsyncdebugoperation"></a>IDebugAsyncOperation::GetSyncDebugOperation
Retourne l’opération de débogage synchrone associée à cet objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetSyncDebugOperation(  
   IDebugSyncOperation**  ppsdo  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppsdo`  
 à Opération de débogage synchrone associée à cet objet.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne l’opération de débogage synchrone associée à cet objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)