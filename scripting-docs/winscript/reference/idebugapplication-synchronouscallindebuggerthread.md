---
title: 'IDebugApplication :: SynchronousCallInDebuggerThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.SynchronousCallInDebuggerThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::SynchronousCallInDebuggerThread
ms.assetid: 9daa1722-f25a-4691-aefc-fd28672fb883
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 134717b6ce30c87ccfb4bbb50ffe958717ae757f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574589"
---
# <a name="idebugapplicationsynchronouscallindebuggerthread"></a>IDebugApplication::SynchronousCallInDebuggerThread
Fournit un mécanisme permettant à l’appelant d’exécuter du code dans le thread du débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SynchronousCallInDebuggerThread(  
   IDebugThreadCall*  pptc,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pptc`  
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
 Les moteurs de langage et les hôtes utilisent généralement cette méthode pour implémenter des objets à thread libre par-dessus leurs implémentations à thread unique.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
 [Interface IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)