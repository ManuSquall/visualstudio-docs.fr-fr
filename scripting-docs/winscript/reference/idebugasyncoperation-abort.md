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
ms.openlocfilehash: b9ca6c5e1498229c84dc28a13cda2cce77b58a4f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573298"
---
# <a name="idebugasyncoperationabort"></a>IDebugAsyncOperation::Abort
Annule une opération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Abort();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode n’accepte aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|S_OK|La méthode a réussi.|  
|E_NOTIMPL|Les opérations ne peuvent pas être annulées.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode est généralement appelée à partir du thread du débogueur pour annuler une opération qui ne répond pas. Cette méthode provoque l’appel de la méthode `InProgressAbort` sur l’objet `IDebugSyncOperation`.  
  
## <a name="see-also"></a>Voir aussi  
   de l' [interface IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)  
 [IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)   
 [IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)