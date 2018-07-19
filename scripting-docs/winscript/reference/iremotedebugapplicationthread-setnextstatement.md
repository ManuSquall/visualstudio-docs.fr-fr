---
title: IRemoteDebugApplicationThread::SetNextStatement | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.SetNextStatement
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::SetNextStatement
ms.assetid: 356766da-f7b7-4e8d-b4f3-2ab8da0609b8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb23fa643f9a2333e17239a74d0da2f75e1ea791
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729149"
---
# <a name="iremotedebugapplicationthreadsetnextstatement"></a>IRemoteDebugApplicationThread::SetNextStatement
Force l’exécution du aussi proche que possible dans le contexte de code donné, dans le contexte de l’image donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pStackFrame`  
 [in] L’objet de frame de pile. Cet argument peut être NULL, ce qui implique le frame de pile en cours doit être utilisé.  
  
 `pCodeContext`  
 [in] Le contexte de code. Cet argument peut être NULL, ce qui implique le contexte de code en cours doit être utilisé.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode force l’exécution continue aussi proche que possible pour le contexte de code spécifié par `pCodeContext`, dans le contexte de l’image spécifiée par `pStackFrame`. Un de ces arguments peuvent être `NULL`, qui représente le frame actuel ou le contexte.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)