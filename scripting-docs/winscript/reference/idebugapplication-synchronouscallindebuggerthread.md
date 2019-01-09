---
title: IDebugApplication::SynchronousCallInDebuggerThread | Microsoft Docs
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
ms.openlocfilehash: b5c2a4d6c23339a396fbc367e68b81bb13c75adc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089945"
---
# <a name="idebugapplicationsynchronouscallindebuggerthread"></a>IDebugApplication::SynchronousCallInDebuggerThread
Fournit un mécanisme pour que l’appelant exécuter du code dans le thread de débogueur.  
  
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
 Moteurs de langage et les hôtes utilisent généralement cette méthode pour implémenter des objets à threads libres sur leurs implémentations de threads uniques.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Interface IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)