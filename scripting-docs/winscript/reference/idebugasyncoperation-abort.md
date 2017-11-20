---
title: IDebugAsyncOperation::Abort | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugAsyncOperation.Abort
apilocation: pdm.dll
helpviewer_keywords: IDebugAsyncOperation::Abort
ms.assetid: 232541c6-81b8-4eb7-96a7-a8e5fe087b31
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 274f09ae2a8851b897a825c32f18091c2f4250d0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperationabort"></a>IDebugAsyncOperation::Abort
Annule une opération.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Abort();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode ne prend aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|S_OK|La méthode a réussi.|  
|E_NOTIMPL|Les opérations ne peut pas être annulées.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode est généralement appelée à partir du thread de débogueur à annuler une opération qui ne répond pas. Cette méthode provoque la `InProgressAbort` méthode sur le `IDebugSyncOperation` objet à appeler.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugAsyncOperation (Interface)](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)   
 [IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)