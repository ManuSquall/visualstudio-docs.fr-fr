---
title: 'IRemoteDebugApplicationThread :: GetState | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.GetState
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::GetState
ms.assetid: 44503a78-efa9-4fbf-98be-a5dcfa329c5a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 42f7f2a292c908b5fe49f1097b0fe56b8b0b11e0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575254"
---
# <a name="iremotedebugapplicationthreadgetstate"></a>IRemoteDebugApplicationThread::GetState
Obtient l’état de ce thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetState(  
   DWORD*  pState  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pState`  
 à Combinaison des indicateurs d’état de thread suivants :  
  
|Constante|valeur|Description|  
|--------------|-----------|-----------------|  
|THREAD_STATE_RUNNING|0x00000001|Le thread est en cours d’exécution.|  
|THREAD_STATE_SUSPENDED|0x00000002|Le thread est suspendu.|  
|THREAD_BLOCKED|0x00000004|Le thread est bloqué.|  
|THREAD_OUT_OF_CONTEXT|0x00000008|Le thread n’a plus de contenu.|  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode obtient l’état de ce thread.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)