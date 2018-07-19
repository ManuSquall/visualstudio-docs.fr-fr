---
title: IDebugExpression::Start | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.Start
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::Start
ms.assetid: a7af3470-62b5-40f0-987d-63b6b22538b3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14d293649e3a6a87c7f594e244378dc2a7e15ac6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727599"
---
# <a name="idebugexpressionstart"></a>IDebugExpression::Start
Commence l’évaluation de l’expression.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Start(  
   IDebugExpressionCallBack*  pdecb  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdecb`  
 [in] Rappel pour signaler lorsque l’évaluation d’expression est terminée. Si ce paramètre est `NULL`, aucun événement n’est déclenché et le client doit interroger l’état de l’expression à l’aide de `QueryIsComplete`.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode commence à l’évaluation de l’expression.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)   
 [Interface IDebugExpression](../../winscript/reference/idebugexpression-interface.md)