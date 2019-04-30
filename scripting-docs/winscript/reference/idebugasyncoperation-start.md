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
ms.openlocfilehash: b3e02869abab65878412f96b77d5782b9717a1b6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821926"
---
# <a name="idebugasyncoperationstart"></a>IDebugAsyncOperation::Start
L’opération asynchrone commencer.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `padocb`  
 L’interface de rappel qui reçoit des événements d’état à partir de cette opération.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_UNEXPECTED`|Une opération est déjà en attente.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode provoque `IDebugSyncOperation::Execute` à être appelée de façon asynchrone dans le thread obtenu à partir de `IDebugSyncOperation::GetTargetThread`. Cette méthode doit être appelée uniquement à partir du thread de débogueur ; Sinon, elle retournera pas jusqu'à ce que l’opération est terminée.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)   
 [IDebugAsyncOperation (Interface)](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)   
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)