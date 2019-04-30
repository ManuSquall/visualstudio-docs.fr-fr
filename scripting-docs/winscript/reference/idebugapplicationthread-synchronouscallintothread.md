---
title: IDebugApplicationThread::SynchronousCallIntoThread | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationThread.SynchronousCallIntoThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::SynchronousCallIntoThread
ms.assetid: 8a91157f-dade-418a-ad02-5607ce12c95c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0c9b89332b55a180220820e8ffe1e030d37a848
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822084"
---
# <a name="idebugapplicationthreadsynchronouscallintothread"></a>IDebugApplicationThread::SynchronousCallIntoThread
Fournit un mécanisme pour que l’appelant s’exécute dans le thread d’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SynchronousCallIntoThread(  
   IDebugThreadCall*  pstcb,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstcb`  
 [in] L’objet à appeler.  
  
 `dwParam1`  
 [in] Premier paramètre à passer à la `IDebugThreadCall::ThreadCallHandler` (méthode).  
  
 `dwParam2`  
 [in] Deuxième paramètre à passer à la `IDebugThreadCall::ThreadCallHandler` (méthode).  
  
 `dwParam3`  
 [in] Troisième paramètre à passer à la `IDebugThreadCall::ThreadCallHandler` (méthode).  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode fournit un mécanisme pour que l’appelant exécuter du code dans le thread de débogueur. Moteurs de langage et les hôtes utilisent généralement cette méthode pour implémenter des objets à threads libres sur leurs implémentations de threads uniques.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugApplicationThread (Interface)](../../winscript/reference/idebugapplicationthread-interface.md)   
 [Interface IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)