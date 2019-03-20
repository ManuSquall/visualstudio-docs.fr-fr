---
title: IDebugExpression::Start | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: e80f3fb8087d39c76f59cf5c6bc8719c1cbaf5e4
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58145042"
---
# <a name="idebugexpressionstart"></a>IDebugExpression::Start
Commence l’évaluation de l’expression.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Start(  
   IDebugExpressionCallBack*  pdecb  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdecb`  
 [in] Rappel pour indiquer lorsque l’évaluation d’expression est terminée. Si ce paramètre est `NULL`, aucun événement n’est déclenché et le client doit interroger l’état de l’expression à l’aide de `QueryIsComplete`.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode commence à la version d’évaluation de l’expression.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)   
 [Interface IDebugExpression](../../winscript/reference/idebugexpression-interface.md)