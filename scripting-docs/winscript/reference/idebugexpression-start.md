---
title: IDebugExpression::Start | Microsoft Docs
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
ms.openlocfilehash: 2c0d7b809f18407bfeb3de59c9cbb6e6e26911ad
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093338"
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