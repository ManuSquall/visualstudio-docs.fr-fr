---
title: IDebugAsyncOperation::QueryIsComplete | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.QueryIsComplete
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::QueryIsComplete
ms.assetid: fcf6e229-4d40-46d9-ab81-d3561bc8e084
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de686f146fded1e4b53914a1de706025f6680ab6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822004"
---
# <a name="idebugasyncoperationqueryiscomplete"></a>IDebugAsyncOperation::QueryIsComplete
Détermine si l’opération de débogage est terminée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT QueryIsComplete();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode ne prend aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|L’opération est terminée.|  
|`S_FALSE`|L’opération n’est pas terminée.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode détermine si l’opération de débogage est terminée.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)