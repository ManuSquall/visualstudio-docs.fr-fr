---
title: IDebugExpression2::EvaluateAsync | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd01cb13b302269a3a6d91fda14713d8a1412a45
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070742"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
Cette méthode évalue l’expression de façon asynchrone.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EvaluateAsync (   
   EVALFLAGS             dwFlags,  
   IDebugEventCallback2* pExprCallback  
);  
```  
  
```csharp  
int EvaluateAsync(  
   enum_EVALFLAGS       dwFlags,   
   IDebugEventCallback2 pExprCallback  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwFlags`  
 [in] Une combinaison d’indicateurs de la [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) énumération qui contrôlent l’évaluation de l’expression.  
  
 `pExprCallback`  
 [in] Ce paramètre est toujours une valeur null.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Un code d’erreur standard est :  
  
|Error|Description|  
|-----------|-----------------|  
|E_EVALUATE_BUSY_WITH_EVALUATION|Une autre expression est en cours d’évaluation et évaluation de l’expression simultanées n’est pas pris en charge.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode doit retourner immédiatement après l’avoir démarré l’évaluation d’expression. Lorsque l’expression est évaluée avec succès, un [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) doivent être envoyés à la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) rappel tel que fourni par le biais d’événement [attacher ](../../../extensibility/debugger/reference/idebugprogram2-attach.md) ou [attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter cette méthode pour une simple `CExpression` objet qui implémente le [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) interface.  
  
```cpp  
HRESULT CExpression::EvaluateAsync(EVALFLAGS dwFlags,  
                                   IDebugEventCallback2* pExprCallback)  
{  
    // Set the aborted state to FALSE  
    // in case the user tries to redo the evaluation after aborting.  
    m_bAborted = FALSE;  
    // Post the WM_EVAL_EXPR message in the message queue of the current thread.  
    // This starts the expression evaluation on a background thread.  
    PostThreadMessage(GetCurrentThreadId(), WM_EVAL_EXPR, 0, (LPARAM) this);  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)