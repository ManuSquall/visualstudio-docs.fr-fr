---
title: IDebugExpression::QueryIsComplete | Microsoft Docs
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
ms.openlocfilehash: 0c74ff962585d4295ea4c2d21a1ee31fdfc817af
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946314"
---
# <a name="idebugexpressionqueryiscomplete"></a>IDebugExpression::QueryIsComplete
Détermine si l’opération est terminée.  
  
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
|`S_OK`|La méthode a réussi et que l’opération est terminée.|  
|`S_FALSE`|L’opération est toujours en attente.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode détermine si l’opération est terminée.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugExpression](../../winscript/reference/idebugexpression-interface.md)