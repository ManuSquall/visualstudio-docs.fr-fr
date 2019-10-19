---
title: 'IRemoteDebugApplicationThread :: suspend | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.Suspend
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::Suspend
ms.assetid: fd5cc874-2970-4092-b1cd-e638775b0e20
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cb5d4d8c541016de71ee1aabffe0b211f850cb7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575473"
---
# <a name="iremotedebugapplicationthreadsuspend"></a>IRemoteDebugApplicationThread::Suspend
Interrompt le thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Suspend(  
   DWORD*  pdwCount  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdwCount`  
 à Le nombre de suspensions pour le thread.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Lorsque cette méthode interrompt le thread, il incrémente le nombre de suspensions.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)