---
title: 'IDebugExpressionCallBack :: onComplete | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpressionCallBack.onComplete
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugExpressionCallBack::onComplete
ms.assetid: d0b89db3-38e7-44e0-93fe-60205f9149dd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1fd142cc7ecbcd984be1943da05fa782260b10f8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576421"
---
# <a name="idebugexpressioncallbackoncomplete"></a>IDebugExpressionCallBack::onComplete
Indique que l’évaluation de l’expression est terminée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onComplete();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode n’accepte aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode est appelée lorsque l’évaluation de l’expression est terminée. La méthode `IDebugExpression::GetResultAsString` peut être appelée à partir de ce gestionnaire d’événements.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugExpressionCallBack](../../winscript/reference/idebugexpressioncallback-interface.md)  
 [IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)