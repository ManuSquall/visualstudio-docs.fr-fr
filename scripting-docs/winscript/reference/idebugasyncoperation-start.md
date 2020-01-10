---
title: IDebugAsyncOperation::Start | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Start
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Start
ms.assetid: a7272364-28e0-48ae-8405-b8bce8a6b9fd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 485eb34ebe200e7f7898d9338effed37cbf2aa10
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573243"
---
# <a name="idebugasyncoperationstart"></a>IDebugAsyncOperation::Start
Entraîne le début de l’opération asynchrone.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `padocb`  
 Interface de rappel qui reçoit les événements d’état de cette opération.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_UNEXPECTED`|Une opération est déjà en attente.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode provoque l’appel de `IDebugSyncOperation::Execute` de façon asynchrone dans le thread obtenu à partir d' `IDebugSyncOperation::GetTargetThread`. Cette méthode doit être appelée uniquement à partir du thread du débogueur ; dans le cas contraire, il ne sera pas retourné tant que l’opération n’est pas terminée.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)   
   de l' [interface IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)  
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)   
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)