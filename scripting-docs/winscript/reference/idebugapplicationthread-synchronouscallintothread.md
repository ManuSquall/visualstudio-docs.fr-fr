---
title: 'IDebugApplicationThread :: SynchronousCallIntoThread | Microsoft Docs'
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
ms.openlocfilehash: d545782f8103d10b38f3eb0d2f149c4ef3b9dc95
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574500"
---
# <a name="idebugapplicationthreadsynchronouscallintothread"></a>IDebugApplicationThread::SynchronousCallIntoThread
Fournit un mécanisme permettant à l’appelant d’exécuter du code dans le thread d’application.  
  
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
 dans Objet à appeler.  
  
 `dwParam1`  
 dans Premier paramètre à passer à la méthode `IDebugThreadCall::ThreadCallHandler`.  
  
 `dwParam2`  
 dans Deuxième paramètre à passer à la méthode `IDebugThreadCall::ThreadCallHandler`.  
  
 `dwParam3`  
 dans Troisième paramètre à passer à la méthode `IDebugThreadCall::ThreadCallHandler`.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode fournit un mécanisme permettant à l’appelant d’exécuter du code dans le thread du débogueur. Les moteurs de langage et les hôtes utilisent généralement cette méthode pour implémenter des objets à thread libre par-dessus leurs implémentations à thread unique.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)  
 [Interface IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)