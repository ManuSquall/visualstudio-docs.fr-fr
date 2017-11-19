---
title: IDebugAsyncOperation::Start | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugAsyncOperation.Start
apilocation: pdm.dll
helpviewer_keywords: IDebugAsyncOperation::Start
ms.assetid: a7272364-28e0-48ae-8405-b8bce8a6b9fd
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd39053e86dce95fa52ba8576814962d13d8b050
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperationstart"></a>IDebugAsyncOperation::Start
L’opération asynchrone commencer.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `padocb`  
 L’interface de rappel qui reçoit les événements de l’état de cette opération.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_UNEXPECTED`|Une opération est déjà en attente.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode provoque `IDebugSyncOperation::Execute` à être appelées de façon asynchrone dans le thread obtenu à partir de `IDebugSyncOperation::GetTargetThread`. Cette méthode doit être appelée uniquement à partir du thread de débogueur ; Sinon, elle retournera pas jusqu'à ce que l’opération est terminée.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)   
 [IDebugAsyncOperation (Interface)](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)   
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)