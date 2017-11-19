---
title: IDebugThreadCall::ThreadCallHandler | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugThreadCall.ThreadCallHandler
apilocation: jscript.dll
helpviewer_keywords: IDebugThreadCall::ThreadCallHandler
ms.assetid: c6d5d9db-bfed-44ec-90bc-46637f7de0ab
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2b7a22026090c8b3b8b7ded4c960ebf92689cd4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugthreadcallthreadcallhandler"></a>IDebugThreadCall::ThreadCallHandler
Gère les appels à exécuter du code dans un autre thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ThreadCallHandler(  
   DWORD_PTR  dwParam1,  
   DWORD_PTR  dwParam2,  
   DWORD_PTR  dwParam3  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwParam1`  
 [in] Le premier paramètre.  
  
 `dwParam2`  
 [in] Le deuxième paramètre.  
  
 `dwParam3`  
 [in] Le troisième paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode gère les appels à exécuter du code dans le thread de débogueur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugThreadCall (Interface)](../../winscript/reference/idebugthreadcall-interface.md)   
 [IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)   
 [IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)