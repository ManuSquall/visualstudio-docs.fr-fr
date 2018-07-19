---
title: IDebugApplication::SynchronousCallInDebuggerThread | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: c7b66b0b085c0fe3abbee3c3b8c5c3f7d252d3b5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725669"
---
# <a name="idebugapplicationsynchronouscallindebuggerthread"></a>IDebugApplication::SynchronousCallInDebuggerThread
Fournit un mécanisme exécuter du code dans le thread de débogueur à l’appelant.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SynchronousCallInDebuggerThread(  
   IDebugThreadCall*  pptc,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pptc`  
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
 Ordinateurs hôtes et les moteurs de langue utilisent généralement cette méthode pour implémenter les objets libres de threads sur leurs implémentations mono-threads uniques.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugApplication (Interface)](../../winscript/reference/idebugapplication-interface.md)   
 [Interface IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)