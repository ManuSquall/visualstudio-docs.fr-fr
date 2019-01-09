---
title: IDebugAsyncOperation::Start | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 099e256496278a33ccae77351641cfdd23447b1f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094781"
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