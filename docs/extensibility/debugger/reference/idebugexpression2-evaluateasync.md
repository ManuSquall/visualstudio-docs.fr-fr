---
title: "IDebugExpression2::EvaluateAsync | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpression2::EvaluateAsync"
helpviewer_keywords: 
  - "IDebugExpression2::EvaluateAsync"
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugExpression2::EvaluateAsync
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette méthode évalue l'expression de façon asynchrone.  
  
## Syntaxe  
  
```cpp#  
HRESULT EvaluateAsync (   
   EVALFLAGS             dwFlags,  
   IDebugEventCallback2* pExprCallback  
);  
```  
  
```c#  
int EvaluateAsync(  
   enum_EVALFLAGS       dwFlags,   
   IDebugEventCallback2 pExprCallback  
);  
```  
  
#### Paramètres  
 `dwFlags`  
 \[in\]  Une combinaison des indicateurs d'énumération d' [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) qui évaluation de l'expression de contrôle.  
  
 `pExprCallback`  
 \[in\]  ce paramètre est toujours une valeur NULL.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne un code d'erreur.  Code d'erreur se déroule comme suit :  
  
|Erreur|Description|  
|------------|-----------------|  
|E\_EVALUATE\_BUSY\_WITH\_EVALUATION|Une autre expression actuellement est évaluée, et l'évaluation d'une expression simultanée n'est pas prise en charge.|  
  
## Notes  
 Cette méthode doit retourner immédiatement après qu'il a démarré l'évaluation de l'expression.  Lorsque l'expression est correctement évaluée, [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) doit être envoyé au rappel d'événement d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) comme indiqué dans [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) ou [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## Exemple  
 L'exemple suivant indique comment appliquer cette méthode d'un objet simple d' `CExpression` qui implémente l'interface d' [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) .  
  
```cpp#  
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
  
## Voir aussi  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)