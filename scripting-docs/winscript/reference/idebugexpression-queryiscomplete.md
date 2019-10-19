---
title: 'IDebugExpression :: QueryIsComplete | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.QueryIsComplete
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::QueryIsComplete
ms.assetid: 510d62e5-a316-46fb-b23f-d3ba902b295c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c260ac5c02052f11f70e479588d65b71b4971267
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571979"
---
# <a name="idebugexpressionqueryiscomplete"></a>IDebugExpression::QueryIsComplete
Détermine si l’opération est terminée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT QueryIsComplete();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode n’accepte aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi et l’opération est terminée.|  
|`S_FALSE`|L’opération est toujours en attente.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode détermine si l’opération est terminée.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugExpression](../../winscript/reference/idebugexpression-interface.md)