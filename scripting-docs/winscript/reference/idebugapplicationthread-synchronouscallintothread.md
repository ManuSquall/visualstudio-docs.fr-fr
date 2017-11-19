---
title: IDebugApplicationThread::SynchronousCallIntoThread | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplicationThread.SynchronousCallIntoThread
apilocation: pdm.dll
helpviewer_keywords: IDebugApplicationThread::SynchronousCallIntoThread
ms.assetid: 8a91157f-dade-418a-ad02-5607ce12c95c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fdeb57380975f19424f8b7da783846b5aae976ed
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthreadsynchronouscallintothread"></a>IDebugApplicationThread::SynchronousCallIntoThread
Fournit un mécanisme exécuter du code dans le thread d’application à l’appelant.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SynchronousCallIntoThread(  
   IDebugThreadCall*  pstcb,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstcb`  
 [in] Objet à appeler.  
  
 `dwParam1`  
 [in] Premier paramètre à passer à la `IDebugThreadCall::ThreadCallHandler` (méthode).  
  
 `dwParam2`  
 [in] Deuxième paramètre à passer à la `IDebugThreadCall::ThreadCallHandler` (méthode).  
  
 `dwParam3`  
 [in] Troisième paramètre à passer à la `IDebugThreadCall::ThreadCallHandler` (méthode).  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode fournit un mécanisme exécuter du code dans le thread de débogueur à l’appelant. Ordinateurs hôtes et les moteurs de langue utilisent généralement cette méthode pour implémenter les objets libres de threads sur leurs implémentations mono-threads uniques.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugApplicationThread (Interface)](../../winscript/reference/idebugapplicationthread-interface.md)   
 [Interface IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)