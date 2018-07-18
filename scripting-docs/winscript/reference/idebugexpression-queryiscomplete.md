---
title: IDebugExpression::QueryIsComplete | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: c1d72b2a2d41b748954f2e4b2b4aa9f0011ca670
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726729"
---
# <a name="idebugexpressionqueryiscomplete"></a>IDebugExpression::QueryIsComplete
Détermine si l’opération est terminée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT QueryIsComplete();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode ne prend aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi et que l’opération est terminée.|  
|`S_FALSE`|L’opération est toujours en attente.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode détermine si l’opération est terminée.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugExpression](../../winscript/reference/idebugexpression-interface.md)