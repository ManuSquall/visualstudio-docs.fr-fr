---
title: IDebugAsyncOperation::Abort | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Abort
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Abort
ms.assetid: 232541c6-81b8-4eb7-96a7-a8e5fe087b31
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be696f852f7038316141415494920c43580738c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822097"
---
# <a name="idebugasyncoperationabort"></a>IDebugAsyncOperation::Abort
Annule une opération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Abort();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode ne prend aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|La méthode a réussi.|  
|E_NOTIMPL|Les opérations ne peut pas être annulées.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode est généralement appelée à partir du thread de débogueur à annuler une opération qui ne répond pas. Cette méthode provoque la `InProgressAbort` méthode sur le `IDebugSyncOperation` objet à appeler.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugAsyncOperation (Interface)](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)   
 [IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)